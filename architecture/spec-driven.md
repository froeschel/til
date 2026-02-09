# Spec-Driven Development

Spec-driven development as the name states, starts with writing the specifications for the software you want to build. The specification then becomes the contract on how the software should work. This approach can be used when developing with AI agents. 
The specification gives the agents a clear input on which functionality to implement. The specification can also be used to create tests in order to verify that the agents have developed the software correctly. 

## Example
Here is an example of a specification. Keep in mind that this is mad for a coding agent.

# Spec: [Short Title]

## Goal
One or two sentences describing the business outcome.

## Context
- **Project(s):** which project(s) in the repo are affected
- **Reference patterns:** existing files I should use as examples
- **Related docs:** links to docs that may need updating

## Constraints
- Things I must NOT change
- Performance/security requirements
- Backward compatibility rules

## Requirements

### R1: [Short name]
- **Description:** What should happen, stated as a fact about the finished system.
- **Affected files:** `src/Foo/Bar.cs` (modify), `src/Foo/Baz.cs` (new file)
- **Acceptance criteria:**
  - [ ] Given X, when Y, then Z
  - [ ] Unit test exists in `tests/Foo.Tests/BarTests.cs`
  - [ ] DI registration updated in `Program.cs`

### R2: [Short name]
- **Description:** ...
- **Affected files:** ...
- **Acceptance criteria:**
  - [ ] ...

## Out of Scope
- Explicitly list things that look related but should NOT be touched.

## Verification
- `dotnet build responza.sln` passes
- `dotnet test tests/*` passes
- Manual smoke test steps (if any)

## Documentation
- List pages on https://docsv2.spitzeco.dk that need updating

