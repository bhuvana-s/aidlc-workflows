# Code Generation - Detailed Steps (TDD Version)

## Overview
This stage generates code for each unit of work through two integrated parts using Test-Driven Development (TDD):
- **Part 1 - Planning**: Create detailed code generation plan with explicit steps
- **Part 2 - Generation**: Execute approved plan to generate tests first, then implementation code

**TDD Approach**: This version follows the Red-Green-Refactor cycle:
1. **Red**: Write failing tests based on acceptance criteria
2. **Green**: Write minimal code to make tests pass
3. **Refactor**: Improve code quality while keeping tests green

**IMPORTANT**: The AI cannot execute tests. After generating tests or implementation, the AI will instruct you to run the tests and report the results. You must verify the red/green state transitions.

## Prerequisites
- Unit Design Generation must be complete for the unit
- NFR Implementation (if executed) must be complete for the unit
- All unit design artifacts must be available
- Unit is ready for code generation
- Testing framework and test infrastructure must be specified in NFR Requirements

---

# PART 1: PLANNING

## Step 1: Analyze Unit Context
- [ ] Read unit design artifacts from Unit Design Generation
- [ ] Read unit story map to understand assigned stories
- [ ] Identify unit dependencies and interfaces
- [ ] Validate unit is ready for code generation
- [ ] **TDD**: Review acceptance criteria from user stories for test case generation

## Step 2: Create Detailed Unit Code Generation Plan (TDD Order)
- [ ] Create explicit steps for unit generation in TDD order:
  - **Test Specifications Generation** (NEW - define test scenarios from acceptance criteria)
  - **Business Logic Unit Testing** (FIRST - write failing tests)
  - Business Logic Generation (SECOND - implement to pass tests)
  - Business Logic Refactoring (THIRD - improve code quality)
  - Business Logic Summary
  - **API Layer Unit Testing** (FIRST - write failing tests)
  - API Layer Generation (SECOND - implement to pass tests)
  - API Layer Refactoring (THIRD - improve code quality)
  - API Layer Summary
  - **Repository Layer Unit Testing** (FIRST - write failing tests)
  - Repository Layer Generation (SECOND - implement to pass tests)
  - Repository Layer Refactoring (THIRD - improve code quality)
  - Repository Layer Summary
  - Database Migration Scripts Generation (if data models exist)
  - **Integration Testing** (verify layers work together)
  - Documentation Generation (API docs, README updates)
  - Deployment Artifacts Generation
- [ ] Number each step sequentially
- [ ] Include story mapping references for this unit
- [ ] Add checkboxes [ ] for each step
- [ ] **TDD**: Emphasize that tests must be written before implementation for each layer

## Step 3: Include Unit Generation Context
- [ ] For this unit, include:
  - Stories implemented by this unit
  - **Acceptance criteria from stories** (source for test cases)
  - Dependencies on other units/services
  - Expected interfaces and contracts
  - Database entities owned by this unit
  - Service boundaries and responsibilities
  - **Testing framework and tools** (from NFR Requirements)

## Step 4: Create Unit Plan Document
- [ ] Save complete plan as `aidlc-docs/construction/plans/{unit-name}-code-generation-plan.md`
- [ ] Include step numbering (Step 1, Step 2, etc.)
- [ ] Include unit context and dependencies
- [ ] Include story traceability
- [ ] **TDD**: Include acceptance criteria mapping to test cases
- [ ] Ensure plan is executable step-by-step
- [ ] Emphasize that this plan is the single source of truth for Code Generation
- [ ] **TDD**: Note that tests will be generated before implementation for each layer

## Step 5: Summarize Unit Plan
- [ ] Provide summary of the unit code generation plan to the user
- [ ] Highlight unit generation approach
- [ ] **TDD**: Explain test-first approach and Red-Green-Refactor cycle
- [ ] Explain step sequence and story coverage
- [ ] Note total number of steps and estimated scope
- [ ] **TDD**: Clarify that all tests will initially fail (red phase) before implementation

## Step 6: Log Approval Prompt
- [ ] Before asking for approval, log the prompt with timestamp in `aidlc-docs/audit.md`
- [ ] Include reference to the complete unit code generation plan
- [ ] Use ISO 8601 timestamp format

## Step 7: Wait for Explicit Approval
- [ ] Do not proceed until the user explicitly approves the unit code generation plan
- [ ] Approval must cover the entire plan and generation sequence
- [ ] **TDD**: Ensure user understands tests will be generated first
- [ ] If user requests changes, update the plan and repeat approval process

## Step 8: Record Approval Response
- [ ] Log the user's approval response with timestamp in `aidlc-docs/audit.md`
- [ ] Include the exact user response text
- [ ] Mark the approval status clearly

## Step 9: Update Progress
- [ ] Mark Code Planning complete in `aidlc-state.md`
- [ ] Update the "Current Status" section
- [ ] Prepare for transition to Code Generation

---

# PART 2: GENERATION

## Step 10: Load Unit Code Generation Plan
- [ ] Read the complete plan from `aidlc-docs/construction/plans/{unit-name}-code-generation-plan.md`
- [ ] Identify the next uncompleted step (first [ ] checkbox)
- [ ] Load the context for that step (unit, dependencies, stories)
- [ ] **TDD**: If current step is test generation, load acceptance criteria

## Step 11: Execute Current Step (TDD-Aware)
- [ ] Perform exactly what the current step describes
- [ ] **If Test Generation Step**:
  - Generate test files with test cases based on acceptance criteria
  - Include test data fixtures and mocks as needed
  - Ensure tests are comprehensive (happy path, edge cases, error cases)
  - **DO NOT generate implementation code yet**
  - Document expected behavior in test descriptions
  - **Note to user**: Tests will fail until implementation is generated (RED phase)
- [ ] **If Implementation Step**:
  - Generate minimal code to make the tests pass
  - Follow the unit's story requirements
  - Respect dependencies and interfaces defined in the plan
  - **Instruct user to run tests** to verify they pass (GREEN phase)
- [ ] **If Refactoring Step**:
  - Improve code quality (readability, maintainability, performance)
  - Remove duplication
  - Apply design patterns where appropriate
  - **Instruct user to run tests** to ensure they still pass after refactoring
- [ ] Follow the unit's story requirements
- [ ] Respect dependencies and interfaces defined in the plan

## Step 12: Update Progress (TDD-Aware)
- [ ] Mark the completed step as [x] in the unit code generation plan
- [ ] **TDD**: After test generation, note that tests should fail until implementation (RED phase expected)
- [ ] **TDD**: After implementation, instruct user to run tests to verify GREEN phase
- [ ] **TDD**: After refactoring, instruct user to run tests to confirm they remain GREEN
- [ ] Mark associated unit stories as [x] when their generation is finished
- [ ] Update `aidlc-docs/aidlc-state.md` current status
- [ ] Save all generated artifacts

## Step 13: Continue or Complete Generation
- [ ] If more steps remain, return to Step 10
- [ ] If all steps complete, proceed to present completion message
- [ ] **TDD**: Remind user to run full test suite to verify all tests pass

## Step 14: Present Completion Message
- Present completion message in this structure:
     1. **Completion Announcement** (mandatory): Always start with this:

```markdown
# 💻 Code Generation Complete - [unit-name] (TDD)
```

     2. **AI Summary** (optional): Provide structured bullet-point summary of code generation
        - Format: "Code generation has created [description]:"
        - List key code artifacts generated (bullet points)
        - **TDD**: List test coverage and test files created (with counts)
        - **TDD**: Note that user should run tests to verify RED-GREEN-REFACTOR cycle
        - **TDD**: Provide command to run tests (e.g., `npm test` or `pytest`)
        - Mention documentation and deployment artifacts
        - DO NOT include workflow instructions ("please review", "let me know", "proceed to next phase", "before we proceed")
        - Keep factual and content-focused
     3. **Formatted Workflow Message** (mandatory): Always end with this exact format:

```markdown
> **📋 <u>**REVIEW REQUIRED:**</u>**  
> Please examine the generated code at: `aidlc-docs/construction/[unit-name]/code/`
> **TDD Note**: Run tests with `[test-command]` to verify RED-GREEN-REFACTOR cycle.



> **🚀 <u>**WHAT'S NEXT?**</u>**
>
> **You may:**
>
> 🔧 **Request Changes** - Ask for modifications to tests or implementation based on your review  
> ✅ **Continue to Next Stage** - After verifying tests pass, approve code generation and proceed to **[next-unit/Build & Test]**

---
```

## Step 15: Wait for Explicit Approval
- Do not proceed until the user explicitly approves the generated code
- Approval must be clear and unambiguous
- **TDD**: User should run tests and verify they pass before approving
- **TDD**: User should confirm test coverage is adequate
- If user requests changes, update the code/tests and repeat the approval process

## Step 16: Record Approval and Update Progress
- Log approval in audit.md with timestamp
- Record the user's approval response with timestamp
- Mark Code Generation stage as complete for this unit in aidlc-state.md

---

## Critical Rules

### Planning Phase Rules
- Create explicit, numbered steps for all generation activities
- **TDD**: Always list test generation before implementation for each layer
- Include story traceability in the plan
- **TDD**: Map acceptance criteria to test cases
- Document unit context and dependencies
- Get explicit user approval before generation

### Generation Phase Rules (TDD-Specific)
- **NO HARDCODED LOGIC**: Only execute what's written in the unit plan
- **FOLLOW PLAN EXACTLY**: Do not deviate from the step sequence
- **TDD RED PHASE**: Generate tests first, user will verify they fail initially
- **TDD GREEN PHASE**: Generate minimal implementation, user will verify tests pass
- **TDD REFACTOR PHASE**: Improve code quality, user will verify tests still pass
- **UPDATE CHECKBOXES**: Mark [x] immediately after completing each step
- **STORY TRACEABILITY**: Mark unit stories [x] when functionality is implemented
- **RESPECT DEPENDENCIES**: Only implement when unit dependencies are satisfied
- **USER VERIFICATION**: Instruct user to run tests at each phase transition
- **NO TEST EXECUTION**: AI cannot run tests - user must verify red/green states

### TDD Best Practices
- Write tests that clearly express intent through descriptive names
- Test one behavior per test case
- Use arrange-act-assert pattern in tests
- Include edge cases and error scenarios in tests
- Mock external dependencies in unit tests
- Keep tests independent and isolated
- Generate test data fixtures for consistent testing
- Document complex test scenarios with comments

## Completion Criteria
- Complete unit code generation plan created and approved
- All steps in unit code generation plan marked [x]
- **TDD**: All test files generated before implementation
- **TDD**: User has run tests and confirmed they pass (green state)
- **TDD**: Code refactored for quality while maintaining passing tests
- All unit stories implemented according to plan
- **TDD**: Test coverage meets acceptance criteria (user verified)
- Deployment artifacts generated
- Complete unit ready for build and verification

## TDD Artifacts Generated

For each unit, the following test artifacts are created:

### Test Files
- `src/{layer}/__tests__/{component}.test.js` - Unit test files
- `src/{layer}/__tests__/fixtures/` - Test data fixtures
- `src/{layer}/__tests__/mocks/` - Mock objects and stubs

### Test Documentation
- Test coverage report (generated during Build & Test)
- Test execution summary (all tests passing)
- Acceptance criteria to test case mapping

### Implementation Files
- Implementation code that passes all tests
- Refactored code maintaining test coverage
