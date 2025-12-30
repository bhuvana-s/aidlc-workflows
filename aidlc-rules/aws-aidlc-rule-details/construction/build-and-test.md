# Build and Test (TDD Version)

**Purpose**: Build all units and execute comprehensive testing strategy

**TDD Context**: When TDD mode was used during Code Generation, unit tests have already been written and verified during development. This stage focuses on integration, performance, and other higher-level testing.

## Prerequisites
- Code Generation must be complete for all units
- All code artifacts must be generated
- **TDD**: Unit tests already exist and have been verified during Code Generation
- Project is ready for build and comprehensive testing

---

## Step 1: Analyze Testing Requirements (TDD-Aware)

Analyze the project to determine appropriate testing strategy:

- **Unit tests**: ✅ Already generated and verified per unit during TDD Code Generation
  - Tests were written before implementation
  - Tests verified in RED-GREEN-REFACTOR cycle
  - Focus: Confirm all unit tests still pass together
  
- **Integration tests**: Test interactions between units/services
  - Focus: How units work together
  - New tests needed for cross-unit scenarios
  
- **Performance tests**: Load, stress, and scalability testing
  - Focus: System behavior under load
  
- **End-to-end tests**: Complete user workflows
  - Focus: Full user journeys across all units
  
- **Contract tests**: API contract validation between services
  - Focus: Service interface compatibility
  
- **Security tests**: Vulnerability scanning, penetration testing
  - Focus: Security posture of complete system

**TDD Note**: Since unit tests were already verified during Code Generation, this stage emphasizes integration and system-level testing.

---

## Step 2: Generate Build Instructions

Create `aidlc-docs/construction/build-and-test/build-instructions.md`:

```markdown
# Build Instructions

## Prerequisites
- **Build Tool**: [Tool name and version]
- **Dependencies**: [List all required dependencies]
- **Environment Variables**: [List required env vars]
- **System Requirements**: [OS, memory, disk space]

## Build Steps

### 1. Install Dependencies
\`\`\`bash
[Command to install dependencies]
# Example: npm install, mvn dependency:resolve, pip install -r requirements.txt
\`\`\`

### 2. Configure Environment
\`\`\`bash
[Commands to set up environment]
# Example: export variables, configure credentials
\`\`\`

### 3. Build All Units
\`\`\`bash
[Command to build all units]
# Example: mvn clean install, npm run build, brazil-build
\`\`\`

### 4. Verify Build Success
- **Expected Output**: [Describe successful build output]
- **Build Artifacts**: [List generated artifacts and locations]
- **Common Warnings**: [Note any acceptable warnings]

## Troubleshooting

### Build Fails with Dependency Errors
- **Cause**: [Common causes]
- **Solution**: [Step-by-step fix]

### Build Fails with Compilation Errors
- **Cause**: [Common causes]
- **Solution**: [Step-by-step fix]
```

---

## Step 3: Generate Unit Test Verification Instructions (TDD Version)

Create `aidlc-docs/construction/build-and-test/unit-test-verification.md`:

```markdown
# Unit Test Verification (TDD)

## Context
Unit tests were already written and verified during TDD Code Generation. This step confirms all unit tests still pass when run together across all units.

## Run All Unit Tests Together

### 1. Execute Complete Unit Test Suite
\`\`\`bash
[Command to run all unit tests across all units]
# Example: npm test, mvn test, pytest tests/unit
\`\`\`

### 2. Review Test Results
- **Expected**: All [X] tests pass (tests already passed individually during TDD)
- **Test Coverage**: [Expected coverage percentage] (should match TDD coverage)
- **Test Report Location**: [Path to test reports]

### 3. TDD Verification Checklist
- [ ] All unit tests from Unit 1 pass
- [ ] All unit tests from Unit 2 pass
- [ ] All unit tests from Unit 3 pass
- [ ] All unit tests from Unit 4 pass
- [ ] No test conflicts between units
- [ ] Test coverage meets target ([X]%)

### 4. If Tests Fail
**This is unexpected** - tests should have passed during TDD Code Generation.

Possible causes:
1. **Integration issue**: Units conflict when combined
2. **Environment issue**: Different environment than during Code Generation
3. **Dependency issue**: Version mismatch or missing dependency
4. **Test isolation issue**: Tests aren't properly isolated

**Resolution**:
1. Identify which unit's tests are failing
2. Check if tests pass when run in isolation
3. If isolated tests pass but combined tests fail → integration issue
4. Fix the issue and rerun all tests

## Test Coverage Report

### Generate Coverage Report
\`\`\`bash
[Command to generate coverage report]
# Example: npm run coverage, mvn jacoco:report, pytest --cov
\`\`\`

### Review Coverage
- **Overall Coverage**: [X]% (should match TDD target)
- **Per-Unit Coverage**:
  - Unit 1: [X]%
  - Unit 2: [X]%
  - Unit 3: [X]%
  - Unit 4: [X]%
- **Coverage Report**: [Path to HTML report]

### TDD Coverage Validation
- [ ] Coverage meets or exceeds target set during TDD
- [ ] All critical paths are covered
- [ ] Edge cases are tested
- [ ] Error scenarios are tested
```

---

## Step 4: Generate Integration Test Instructions

Create `aidlc-docs/construction/build-and-test/integration-test-instructions.md`:

```markdown
# Integration Test Instructions

## Purpose
Test interactions between units/services to ensure they work together correctly.

**TDD Note**: Unit tests verified individual components. Integration tests verify how components interact.

## Test Scenarios

### Scenario 1: [Unit A] → [Unit B] Integration
- **Description**: [What is being tested]
- **Setup**: [Required test environment setup]
- **Test Steps**: [Step-by-step test execution]
- **Expected Results**: [What should happen]
- **Cleanup**: [How to clean up after test]

### Scenario 2: [Unit B] → [Unit C] Integration
[Similar structure]

## Setup Integration Test Environment

### 1. Start Required Services
\`\`\`bash
[Commands to start services]
# Example: docker-compose up, start test database
\`\`\`

### 2. Configure Service Endpoints
\`\`\`bash
[Commands to configure endpoints]
# Example: export API_URL=http://localhost:8080
\`\`\`

## Run Integration Tests

### 1. Execute Integration Test Suite
\`\`\`bash
[Command to run integration tests]
# Example: mvn integration-test, npm run test:integration
\`\`\`

### 2. Verify Service Interactions
- **Test Scenarios**: [List key integration test scenarios]
- **Expected Results**: [Describe expected outcomes]
- **Logs Location**: [Where to check logs]

### 3. Cleanup
\`\`\`bash
[Commands to clean up test environment]
# Example: docker-compose down, stop test services
\`\`\`

## Integration Test Results
- **Total Scenarios**: [X]
- **Passed**: [X]
- **Failed**: [X]
- **Status**: [Pass/Fail]
```

---

## Step 5: Generate Performance Test Instructions (If Applicable)

Create `aidlc-docs/construction/build-and-test/performance-test-instructions.md`:

[Same as standard version - performance testing is independent of TDD]

---

## Step 6: Generate Additional Test Instructions (As Needed)

Based on project requirements, generate additional test instruction files:

### Contract Tests (For Microservices)
Create `aidlc-docs/construction/build-and-test/contract-test-instructions.md`

### Security Tests
Create `aidlc-docs/construction/build-and-test/security-test-instructions.md`

### End-to-End Tests
Create `aidlc-docs/construction/build-and-test/e2e-test-instructions.md`

---

## Step 7: Generate Test Summary (TDD Version)

Create `aidlc-docs/construction/build-and-test/build-and-test-summary.md`:

```markdown
# Build and Test Summary (TDD)

## Build Status
- **Build Tool**: [Tool name]
- **Build Status**: [Success/Failed]
- **Build Artifacts**: [List artifacts]
- **Build Time**: [Duration]

## Test Execution Summary

### Unit Tests (TDD Verified)
- **Total Tests**: [X]
- **Passed**: [X]
- **Failed**: [X]
- **Coverage**: [X]%
- **Status**: [Pass/Fail]
- **TDD Note**: Tests were written before implementation and verified during Code Generation

### Integration Tests
- **Test Scenarios**: [X]
- **Passed**: [X]
- **Failed**: [X]
- **Status**: [Pass/Fail]
- **Focus**: Cross-unit interactions

### Performance Tests
- **Response Time**: [Actual] (Target: [Expected])
- **Throughput**: [Actual] (Target: [Expected])
- **Error Rate**: [Actual] (Target: [Expected])
- **Status**: [Pass/Fail]

### Additional Tests
- **Contract Tests**: [Pass/Fail/N/A]
- **Security Tests**: [Pass/Fail/N/A]
- **E2E Tests**: [Pass/Fail/N/A]

## TDD Quality Metrics
- **Test-First Coverage**: [X]% (code written after tests)
- **Refactoring Safety**: All tests passed after refactoring
- **RED-GREEN-REFACTOR**: Verified for all [X] components

## Overall Status
- **Build**: [Success/Failed]
- **All Tests**: [Pass/Fail]
- **TDD Quality**: [High/Medium/Low]
- **Ready for Operations**: [Yes/No]

## Next Steps
[If all pass]: Ready to proceed to Operations phase for deployment planning
[If failures]: Address failing tests and rebuild
```

---

## Step 8: Update State Tracking

Update `aidlc-docs/aidlc-state.md`:
- Mark Build and Test stage as complete
- Note TDD approach was used
- Update current status

---

## Step 9: Present Results to User (TDD Version)

Present comprehensive message:

```
"🔨 Build and Test Complete (TDD)!

**Build Status**: [Success/Failed]

**Test Results**:
✅ Unit Tests: [X] passed (TDD-verified during Code Generation)
✅ Integration Tests: [X] scenarios passed
✅ Performance Tests: [Status]
✅ Additional Tests: [Status]

**TDD Quality**:
✅ All unit tests written before implementation
✅ RED-GREEN-REFACTOR cycle verified for all components
✅ Test coverage: [X]% (meets TDD target)
✅ Refactoring safety confirmed

**Generated Files**:
1. ✅ build-instructions.md
2. ✅ unit-test-verification.md (TDD version)
3. ✅ integration-test-instructions.md
4. ✅ performance-test-instructions.md (if applicable)
5. ✅ [additional test files as needed]
6. ✅ build-and-test-summary.md (TDD version)

Review the summary in aidlc-docs/construction/build-and-test/build-and-test-summary.md

**TDD Benefits Realized**:
- High test coverage from day one
- Tests document expected behavior
- Refactoring was safe due to comprehensive tests
- Integration issues caught early

**Ready to proceed to Operations stage for deployment planning?**"
```

---

## Step 10: Log Interaction

**MANDATORY**: Log the phase completion in `aidlc-docs/audit.md`:

```markdown
## Build and Test Stage (TDD)
**Timestamp**: [ISO timestamp]
**Build Status**: [Success/Failed]
**Test Status**: [Pass/Fail]
**TDD Approach**: Unit tests written before implementation during Code Generation
**Test Coverage**: [X]%
**Files Generated**:
- build-instructions.md
- unit-test-verification.md (TDD version)
- integration-test-instructions.md
- performance-test-instructions.md
- build-and-test-summary.md (TDD version)

---
```

---

## Key Differences from Standard Build and Test

### What's Different

1. **Unit Test Focus**:
   - Standard: Generate and run unit tests
   - TDD: Verify existing unit tests still pass together

2. **Test Confidence**:
   - Standard: First time running all tests
   - TDD: Tests already verified during development

3. **Coverage**:
   - Standard: Measure coverage after the fact
   - TDD: Confirm coverage matches TDD target

4. **Integration Emphasis**:
   - Standard: Equal focus on unit and integration
   - TDD: More emphasis on integration (units already tested)

5. **Documentation**:
   - Standard: unit-test-instructions.md
   - TDD: unit-test-verification.md (different focus)

### What's the Same

- Build process
- Integration testing
- Performance testing
- Security testing
- E2E testing
- Overall structure

### Why This Matters

With TDD:
- Unit tests are more trustworthy (written first, verified during development)
- Integration testing becomes more important (units are solid, focus on interactions)
- Test failures are more likely integration issues than unit issues
- Coverage is higher and more meaningful
- Refactoring was already safe (tests existed before refactoring)

---

## Troubleshooting TDD-Specific Issues

### Issue: Unit Tests Fail in Build and Test (But Passed During TDD)

**Possible Causes**:
1. Tests aren't isolated - they depend on execution order
2. Shared state between tests
3. Environment differences
4. Dependency version mismatch

**Resolution**:
1. Run tests in random order to check isolation
2. Check for global state or shared resources
3. Verify environment matches Code Generation environment
4. Lock dependency versions

### Issue: Lower Coverage Than Expected

**Possible Causes**:
1. Some code wasn't generated through TDD
2. Coverage tool configuration changed
3. New code added without tests

**Resolution**:
1. Review which code lacks coverage
2. Verify coverage tool settings
3. Add tests for uncovered code

### Issue: Integration Tests Fail (But Unit Tests Pass)

**Expected** - This is what integration tests are for!

**Resolution**:
1. Identify which units aren't integrating correctly
2. Check interface contracts between units
3. Verify data flow between units
4. Add integration tests to prevent regression
