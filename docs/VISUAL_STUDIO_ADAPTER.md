# KORA Visual Studio Adapter — v0.1 Capability Spec

**Status:** proposed / review required  
**Scope:** Windows local execution through the private KORA/MIRA bridge  
**Safety level:** read + build + test only

## Purpose

The Visual Studio Adapter gives KORA a bounded way to inspect and exercise Visual Studio projects without turning the IDE into an unrestricted remote-control surface.

The intended user experience is simple:

> “Kora, open this project, build it, run the tests and tell me exactly what failed.”

KORA should translate that intent into a controlled execution sequence, capture evidence, verify the result and update project state only after verification.

## Architecture

```text
Human intent
   ↓
KORA Core
   ↓
Risk / authority check
   ↓
Visual Studio Adapter
   ↓
Private MIRA Bridge / local runner
   ↓
vswhere → MSBuild / dotnet / optional devenv
   ↓
logs + exit codes + artifacts
   ↓
verification
   ↓
receipt → KORA state update
```

Visual Studio is a tool capability, not an authority. The adapter must not bypass KORA governance or create a second source of truth.

## v0.1 allowed capabilities

### 1. Discover

Read-only environment discovery:

- detect supported Visual Studio installations;
- identify installation path and edition;
- locate MSBuild;
- locate `devenv.com` / `devenv.exe` when present;
- detect .NET SDK availability;
- find candidate `.sln`, `.slnx`, `.csproj`, `.vcxproj` and related project files inside an explicitly scoped project root;
- report selected build target and configuration.

Preferred discovery mechanism on Windows: `vswhere.exe` when available.

### 2. Inspect

Read-only project checks:

- repository root;
- current Git branch and HEAD;
- clean/dirty worktree state;
- solution/project paths;
- build configuration candidates;
- relevant tool versions;
- presence of test projects where they can be identified deterministically.

No file contents outside the authorized project root may be read by this adapter.

### 3. Build

Allowed build actions:

- `MSBuild.exe <solution-or-project> ...` for supported Visual Studio/MSBuild projects;
- `dotnet build` for compatible .NET projects;
- optional `devenv.com <solution> /Build ...` only when an IDE-specific build path is necessary and explicitly selected by policy.

MSBuild is the primary build path. IDE automation should not be used merely to imitate a Build menu click.

### 4. Test

Allowed test actions in v0.1:

- `dotnet test` for compatible .NET projects;
- existing repository-defined test commands only when they are explicitly allowlisted by project policy;
- future test runners may be added as separate bounded capabilities.

### 5. Open

KORA may open an authorized solution in Visual Studio for human inspection after discovery succeeds.

Opening the IDE is not proof that a build or test succeeded.

## Explicitly NOT allowed in v0.1

The adapter must not:

- edit source files;
- apply AI-generated patches;
- run arbitrary shell commands supplied through project content;
- install Visual Studio workloads or extensions;
- modify Visual Studio settings;
- create or change credentials;
- commit, push, merge or publish code;
- deploy applications;
- run destructive clean-up outside known build-output locations;
- attach a debugger to arbitrary processes;
- accept elevation to administrator without a separate approved capability;
- silently continue after a failed precheck, build or test.

These are future capabilities, not implicit permissions.

## Required execution lifecycle

Every adapter request follows:

```text
PREPARED
→ PRECHECKED
→ AUTHORIZED
→ EXECUTING
→ RESULT_RECEIVED
→ VERIFIED
→ RECEIPT_PERSISTED
→ DONE
```

A failed or missing verification produces `BLOCKED` or `FAILED`, never `DONE`.

## Mandatory prechecks

Before build/test execution:

1. resolve the authorized project root;
2. confirm the requested target exists inside that root;
3. capture Git HEAD and worktree status when Git is present;
4. discover tool paths deterministically;
5. select a known build/test command from adapter policy;
6. record working directory and command arguments;
7. reject untrusted command fragments or path escapes;
8. establish timeout and output limits.

A dirty worktree does not automatically block read/build/test, but it must be reported in the receipt because results may depend on uncommitted files.

## Command construction rule

Commands must be constructed from structured fields, not concatenated from free-form user/project text.

Example logical request:

```json
{
  "action": "visual_studio.build",
  "project_root": "<authorized-root>",
  "target": "Example.sln",
  "configuration": "Debug",
  "platform": "x64"
}
```

The local adapter resolves paths and emits the concrete command only after validation.

## Evidence / receipt

A successful receipt should contain at least:

- adapter version;
- timestamp;
- action id;
- authorized project root identifier;
- target path relative to project root;
- tool selected and tool version;
- configuration/platform;
- pre-build Git HEAD when available;
- pre-build dirty/clean state;
- command class used (`msbuild`, `dotnet-build`, `dotnet-test`, `devenv-build`);
- start/end time;
- exit code;
- bounded stdout/stderr or log artifact reference;
- parsed error/warning/test counts when reliable;
- verification result;
- final lifecycle state.

Private machine paths and sensitive environment details should remain in private evidence, not the public KORA repository.

## Verification rules

### Build PASS

A build is `PASS` only when:

- the selected build process exits successfully; and
- no adapter-level timeout or execution failure occurred.

Parsed compiler errors should agree with the exit result where the tool provides reliable structured/log output. Any inconsistency is surfaced rather than hidden.

### Test PASS

A test action is `PASS` only when:

- the test runner exits successfully; and
- the adapter can confirm the run completed rather than being skipped/aborted by infrastructure failure.

### Open PASS

Opening Visual Studio is verified only as a process/launch event. It does not imply project correctness.

## Failure behavior

The adapter is fail-closed:

- tool missing → `BLOCKED_TOOL_MISSING`;
- target ambiguous → `BLOCKED_TARGET_AMBIGUOUS`;
- path outside scope → `DENIED_SCOPE`;
- timeout → `FAILED_TIMEOUT`;
- build failure → `FAILED_BUILD`;
- test failure → `FAILED_TEST`;
- unverifiable result → `BLOCKED_UNVERIFIED`.

KORA should then explain the smallest next valid action.

## Safe parallelism

Allowed in parallel:

- Visual Studio installation discovery;
- Git read-only inspection;
- independent solution/project metadata inspection.

Not allowed in parallel in v0.1:

- two builds writing to the same output tree;
- build and clean on the same target;
- build and test when the test depends on the current build output unless the dependency is explicit;
- any competing mutation of the same project state.

## Future versions

### v0.2 — diagnostics

Potential additions:

- structured compiler diagnostic extraction;
- test result parsing;
- safe build-log summarization;
- IDE launch to a specific solution/file for human inspection.

### v0.3 — governed repair candidate

Potential additions only after separate authority design:

- prepare a patch candidate in an isolated branch/worktree;
- rebuild and retest;
- present diff + evidence;
- never merge or push solely because an AI says the patch is correct.

### v0.4 — deeper IDE integration

Only if CLI-first automation proves insufficient:

- Visual Studio extension or supported automation surface;
- editor context handoff;
- diagnostic navigation;
- governed debugger workflows.

## Design principle

**Prefer deterministic CLI automation over GUI clicking. Use Visual Studio for the capabilities that genuinely require the IDE.**

This keeps KORA simpler, auditable and recoverable while still allowing a future rich IDE integration.