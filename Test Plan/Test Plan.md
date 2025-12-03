# Test Plan Document
## HMRC Payroll System QA Project

---

### Document Control

| Field | Details |
|-------|---------|
| **Document Title** | HMRC Payroll System - Test Plan |
| **Version** | 1.0 |
| **Prepared By** | Kishan Thapa |
| **Role** | QA Engineer |
| **Date Prepared** | YYYY/MM/DD |
| **Last Updated** | YYYY/MM/DD |
| **Status** | Draft / Under Review / Approved |

### Document History

| Version | Date | Author | Changes Made | Approver |
|---------|------|--------|--------------|----------|
| 0.1 | YYYY/MM/DD | Kishan Thapa | Initial Draft | - |
| 1.0 | YYYY/MM/DD | Kishan Thapa | Final Version | QA Lead |

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Objectives](#objectives)
3. [Scope](#scope)
4. [Test Strategy](#test-strategy)
5. [Testing Approach](#testing-approach)
6. [Test Environment](#test-environment)
7. [Test Data Management](#test-data-management)
8. [Defect Management](#defect-management)
9. [Test Deliverables](#test-deliverables)
10. [Test Schedule](#test-schedule)
11. [Roles & Responsibilities](#roles-responsibilities)
12. [Risk & Mitigation](#risk-mitigation)
13. [Dependencies & Assumptions](#dependencies-assumptions)
14. [Entry & Exit Criteria](#entry-exit-criteria)
15. [Suspension & Resumption Criteria](#suspension-resumption-criteria)
16. [Metrics & Reporting](#metrics-reporting)
17. [Communication Plan](#communication-plan)
18. [Approval](#approval)

---

## 1. Project Overview

The HMRC Payroll QA Project aims to validate the accuracy, reliability, and compliance of payroll calculations for UK tax regulations. The system calculates Tax (PAYE), National Insurance (NI), Pension contributions, Personal Allowance, and Student Loan deductions, ensuring accurate net pay computation while maintaining data integrity across all system components.

### System Architecture
- **Frontend**: React-based web application
- **Backend**: Microsoft Dynamics CRM
- **Database**: Microsoft Dataverse
- **Integration Layer**: REST APIs for data exchange
- **Reporting**: Payslip generation module

### Stakeholders
- **Project Sponsor**: [Name/Department]
- **Project Manager**: [Name]
- **Development Team Lead**: [Name]
- **QA Lead**: [Name]
- **Business Analyst**: [Name]
- **End Users**: HR/Payroll Department

### Compliance Standards
- HMRC PAYE regulations (as of 2024/2025 tax year)
- UK National Insurance contribution rules
- UK Pension Auto-Enrolment regulations
- Student Loan Plan 1/2/4 deduction rules
- GDPR compliance for employee data handling

---

## 2. Objectives

### Primary Objectives
- Verify accurate payroll calculations for all employees across different tax codes (e.g., 1257L, BR, D0, NT) and NI categories (A, B, C, H, M, Z)
- Ensure correct deductions for Pension, Student Loan Plans (1/2/4), and Personal Allowance
- Validate net pay accuracy against statutory requirements
- Ensure data consistency and integrity across frontend, backend, CRM, and database layers
- Verify API functionality for payroll data transmission

### Secondary Objectives
- Identify functional defects, edge cases, and system errors
- Ensure system handles boundary conditions appropriately
- Validate system performance under normal load conditions
- Provide comprehensive test documentation and evidence
- Establish baseline metrics for future regression testing

---

## 3. Scope

### In Scope

| Category | Details |
|----------|---------|
| **Functional Testing** | Payroll input validation, gross-to-net calculations, tax/NI/pension/student loan deductions, personal allowance calculations, payslip generation accuracy |
| **Integration Testing** | Frontend-Backend integration, API endpoint validation, Dataverse data consistency |
| **Data Validation** | SQL queries to verify data integrity, cross-reference with Excel calculations |
| **Regression Testing** | Retest after defect fixes and code changes |
| **Edge Case Testing** | Negative scenarios, boundary values, mid-month joiners/leavers, pro-rata calculations |
| **Compliance Testing** | Verify adherence to HMRC tax rules and regulations |
| **API Testing** | Postman-based validation of REST API endpoints |

### Out of Scope

| Item | Reason |
|------|--------|
| Real HMRC Gateway Integration | Mock/stub services will be used in test environment |
| UI/UX Design Validation | Design review is handled separately |
| Performance Testing (Load/Stress) | Planned for separate performance testing phase |
| Security Penetration Testing | Handled by dedicated security team |
| Automated Test Script Development | Manual testing approach for initial release; automation planned for future iterations |
| Third-party Pension Provider Integration | Out of current project scope |

---

## 4. Test Strategy

### Testing Levels
1. **Unit Testing** - Performed by Development Team (out of QA scope)
2. **Integration Testing** - QA Team validates API and database integration
3. **System Testing** - End-to-end payroll workflow validation
4. **User Acceptance Testing (UAT)** - Performed by HR/Payroll team (QA provides support)

### Testing Types
- **Functional Testing**: Validate business requirements
- **Regression Testing**: Ensure existing functionality remains intact after changes
- **Integration Testing**: Verify inter-module data flow
- **Boundary/Edge Case Testing**: Test extreme values and conditions
- **Negative Testing**: Invalid inputs and error handling
- **Data Validation Testing**: Backend data integrity checks

### Test Design Techniques
- **Equivalence Partitioning**: Group similar test inputs
- **Boundary Value Analysis**: Test edge values
- **Decision Table Testing**: Complex business rule validation
- **Error Guessing**: Experience-based testing for defect-prone areas

---

## 5. Testing Approach

### 5.1 Functional Testing
- Validate all payroll input fields (employee details, salary, hours worked, deductions)
- Verify gross-to-net salary calculations
- Check deductions for Tax, NI, Pension, Student Loan, and Personal Allowance
- Validate payslip generation with correct values and formatting

### 5.2 Boundary Testing / Edge Cases
- Zero salary or zero working hours
- Negative values (error handling)
- Maximum salary thresholds
- Mid-month joiners and leavers (pro-rata calculations)
- Employees with multiple jobs (cumulative tax)
- Bonus-only payroll periods
- Tax code changes mid-year
- Unpaid leave scenarios

### 5.3 Integration Testing
- Verify React frontend correctly sends data to CRM backend
- Validate Dataverse stores accurate payroll records
- Check API endpoints return correct payroll data
- Ensure data synchronization across all layers

### 5.4 Regression Testing
- Execute regression test suite after each defect fix
- Retest impacted modules after code changes
- Maintain regression test pack for critical workflows

### 5.5 Manual Validation
- Cross-check payroll calculations using Excel formulas
- Verify calculations against HMRC tax calculators
- Document evidence with screenshots and calculation sheets

---

## 6. Test Environment

### Infrastructure

| Component | Specification |
|-----------|---------------|
| **Operating System** | Windows 11 Pro (64-bit) |
| **Browser** | Chrome (latest), Edge (latest), Firefox (latest) |
| **Database** | Microsoft Dataverse (cloud-hosted) |
| **API Testing Tool** | Postman v10.x or later |
| **Spreadsheet Tool** | Microsoft Excel 2021 / Microsoft 365 |
| **Test Management Tool** | Azure DevOps |
| **Version Control** | GitHub |
| **Frontend** | React App (Development/Staging environment) |
| **Backend** | Microsoft Dynamics CRM (Staging instance) |
| **Network** | Corporate VPN (if required) |

### Environment Access
- Test environment URL: [https://test-payroll.company.com]
- Database access: SQL query permissions via authorized accounts
- API endpoints: Staging environment base URL
- Test user accounts: Provided by IT department

### Environment Refresh
- Test data will be refreshed weekly from production (anonymized)
- Environment rebuild: As needed, coordinated with DevOps team

---

## 7. Test Data Management

### Data Requirements
- Employees across all tax codes: 1257L, BR, D0, NT, K codes, Emergency tax codes
- NI categories: A, B, C, H, M, Z
- Various salary ranges: £12,570 to £150,000+ annually
- Student loan plans: Plan 1, Plan 2, Plan 4, Postgraduate
- Pension contribution rates: 3%, 5%, 8%, custom percentages

### Data Sources
- Anonymized production data (GDPR compliant)
- Synthetic test data generated for edge cases
- Excel-based calculation sheets for validation

### Data Security
- No real employee PII used in testing
- Test data follows data masking policies
- Secure disposal of test data post-project

### Data Preparation
- Test data prepared and approved before test execution
- Data traceability maintained for audit purposes

---

## 8. Defect Management

### Defect Lifecycle
1. **New** - Defect logged
2. **Assigned** - Assigned to developer
3. **In Progress** - Developer working on fix
4. **Fixed** - Developer completed fix
5. **Ready for Retest** - Build deployed to test environment
6. **Retest** - QA retesting
7. **Closed** - Defect verified as fixed
8. **Reopened** - If defect persists

### Severity & Priority Definitions

**Severity Levels:**
- **Critical (S1)**: System crash, incorrect payroll calculations affecting all employees, data corruption
- **High (S2)**: Incorrect calculation for specific scenarios, major functionality not working
- **Medium (S3)**: Minor calculation errors, workaround available
- **Low (S4)**: Cosmetic issues, minor UI defects

**Priority Levels:**
- **P1 - Immediate**: Fix required before any release
- **P2 - High**: Fix required before production release
- **P3 - Medium**: Fix in next release/sprint
- **P4 - Low**: Fix when time permits

### Defect Reporting Tool
- Azure DevOps (Bug work item type)

### Defect Report Contents
- Clear title and description
- Steps to reproduce
- Expected vs actual results
- Screenshots/screen recordings
- Test data used
- Environment details
- Severity and priority
- Logs (if applicable)

---

## 9. Test Deliverables

| Deliverable | Description | Owner | Delivery Date |
|-------------|-------------|-------|---------------|
| Test Plan | This document | QA Engineer | YYYY/MM/DD |
| Test Scenarios | High-level test scenarios list | QA Engineer | YYYY/MM/DD |
| Test Cases | Detailed test case documents | QA Engineer | YYYY/MM/DD |
| Test Data | Employee data sets for testing | QA Engineer | YYYY/MM/DD |
| Traceability Matrix | Requirements-to-test case mapping | QA Engineer | YYYY/MM/DD |
| API Test Collection | Postman JSON collection | QA Engineer | YYYY/MM/DD |
| Excel Validation Sheets | Calculation verification | QA Engineer | YYYY/MM/DD |
| Defect Reports | Bug documentation in Azure DevOps | QA Engineer | Ongoing |
| Test Execution Report | Daily/weekly execution summary | QA Engineer | Daily/Weekly |
| Test Summary Report | Final test closure report | QA Engineer | YYYY/MM/DD |
| Test Evidence | Screenshots, logs, recordings | QA Engineer | Ongoing |

---

## 10. Test Schedule

| Activity | Start Date | End Date | Duration | Dependencies |
|----------|-----------|----------|----------|--------------|
| Test Plan Preparation | YYYY/MM/DD | YYYY/MM/DD | 3 days | Requirements signed off |
| Test Environment Setup | YYYY/MM/DD | YYYY/MM/DD | 2 days | Infrastructure team |
| Test Data Preparation | YYYY/MM/DD | YYYY/MM/DD | 2 days | Test plan approved |
| Test Case Design | YYYY/MM/DD | YYYY/MM/DD | 5 days | Test plan approved |
| Test Case Review | YYYY/MM/DD | YYYY/MM/DD | 2 days | Test cases completed |
| Test Execution - Cycle 1 | YYYY/MM/DD | YYYY/MM/DD | 7 days | Code deployed to test env |
| Defect Reporting & Retest | YYYY/MM/DD | YYYY/MM/DD | 5 days | Defects fixed |
| Test Execution - Cycle 2 | YYYY/MM/DD | YYYY/MM/DD | 5 days | Critical defects resolved |
| Regression Testing | YYYY/MM/DD | YYYY/MM/DD | 3 days | All fixes deployed |
| Test Summary Report | YYYY/MM/DD | YYYY/MM/DD | 2 days | Testing completed |
| Sign-off & Closure | YYYY/MM/DD | YYYY/MM/DD | 1 day | Report approved |

**Total Testing Duration**: [X] weeks

---

## 11. Roles & Responsibilities

| Role | Name | Responsibilities |
|------|------|------------------|
| **QA Lead** | [Name] | Approve test plan and strategy, review test cases, monitor test execution, approve test closure, escalate risks and issues |
| **QA Engineer** | Kishan Thapa | Design test scenarios and cases, prepare test data, execute test cases, log and track defects, perform retesting, document results, provide daily status updates |
| **Business Analyst** | [Name] | Provide functional clarifications, validate business requirements, support UAT |
| **Developer** | [Name] | Fix defects, provide technical support, deploy fixes to test environment |
| **DevOps Engineer** | [Name] | Maintain test environment, deploy builds, provide infrastructure support |
| **Project Manager** | [Name] | Track project progress, manage timelines, facilitate communication, approve budget and resources |
| **Consultant** | [Name] | Provide domain expertise on HMRC payroll rules, review test scenarios for compliance |

---

## 12. Risk & Mitigation

| Risk | Impact | Probability | Mitigation Strategy | Owner |
|------|--------|-------------|---------------------|-------|
| Incorrect payroll calculation logic | High | Medium | Cross-verify with Excel calculations and HMRC calculators; involve payroll SME in test case review | QA Engineer |
| Dataverse data inconsistency | High | Low | Validate backend data with SQL queries; implement data integrity checks | QA Engineer |
| API failures or timeouts | Medium | Medium | Use Postman for comprehensive API testing; implement retry logic testing | QA Engineer |
| Test environment unavailability | High | Low | Coordinate with DevOps for scheduled maintenance; have backup environment | DevOps |
| Incomplete test coverage | Medium | Medium | Maintain requirements traceability matrix; conduct peer review of test cases | QA Lead |
| Test data not representative | Medium | Low | Use combination of production-like and synthetic data; validate with BA | QA Engineer |
| Resource unavailability (QA) | High | Low | Cross-train team members; document all testing procedures | QA Lead |
| Changing requirements | Medium | Medium | Implement change control process; assess impact on testing schedule | PM |
| HMRC regulation changes | High | Low | Monitor HMRC updates; maintain flexible test case design | Consultant |
| Defect fix delays | Medium | Medium | Prioritize critical defects; maintain clear communication with dev team | QA Lead |

---

## 13. Dependencies & Assumptions

### Dependencies
- Availability of test environment by [Date]
- Completion of development by [Date]
- Access to Dataverse with appropriate permissions
- Availability of Business Analyst for requirement clarifications
- Developer availability for defect fixes
- Test data provisioning by IT team
- API documentation provided by development team

### Assumptions
- Test environment mirrors production configuration
- HMRC tax rates remain stable during testing period
- All testing will be performed manually for initial release
- Adequate test data representing all scenarios will be available
- Internet connectivity is stable and available
- Required software licenses (Excel, Postman, Azure DevOps) are available
- One QA resource (Kishan Thapa) allocated full-time for testing
- Development team provides fixes within 2 business days for critical defects
- UAT will be conducted by end users post-QA sign-off

---

## 14. Entry & Exit Criteria

### Entry Criteria
- [ ] Test Plan reviewed and approved by QA Lead
- [ ] Test environment deployed and accessible
- [ ] Test data prepared and loaded
- [ ] Requirements document signed off and baselined
- [ ] Build deployed to test environment with release notes
- [ ] Unit testing completed by development team (>80% code coverage)
- [ ] Test cases reviewed and approved
- [ ] API documentation available
- [ ] Database access credentials provided
- [ ] No Severity 1 defects open from previous cycle

### Exit Criteria
- [ ] All planned test cases executed (100% execution)
- [ ] Test case pass rate ≥ 95%
- [ ] Zero Severity 1 (Critical) defects open
- [ ] ≤ 5% Severity 2 (High) defects open (with documented workarounds)
- [ ] All Severity 3 and 4 defects documented for future releases
- [ ] Requirements traceability matrix shows 100% coverage
- [ ] Regression test suite executed successfully
- [ ] Test Summary Report completed and reviewed
- [ ] Test evidence (screenshots, logs) archived
- [ ] Outstanding defects reviewed and accepted by stakeholders
- [ ] QA Lead and Project Manager sign-off obtained

---

## 15. Suspension & Resumption Criteria

### Suspension Criteria
Testing activities will be suspended if:
- More than 10 Severity 1 defects identified in a single test cycle
- Test environment unavailable for more than 24 hours
- Critical third-party service unavailable
- Major requirement changes requiring test case redesign
- Data corruption or security breach in test environment
- Inadequate resources to continue testing

### Resumption Criteria
Testing activities will resume when:
- All Severity 1 defects fixed and verified
- Test environment restored and validated
- New requirements documented and test cases updated accordingly
- Test data integrity verified
- QA Lead approval obtained
- Resource constraints resolved

---

## 16. Metrics & Reporting

### Key Metrics

| Metric | Formula | Target |
|--------|---------|--------|
| **Test Coverage** | (Test Cases / Requirements) × 100 | 100% |
| **Test Execution Progress** | (Executed / Total Test Cases) × 100 | Track daily |
| **Pass Rate** | (Passed / Executed) × 100 | ≥ 95% |
| **Defect Density** | Total Defects / Total Test Cases | < 0.3 |
| **Defect Detection Rate** | Defects Found per Day | Track daily |
| **Defect Resolution Rate** | Defects Fixed per Day | Track daily |
| **Defect Leakage** | Defects found in UAT / Total Defects | < 10% |
| **Requirement Coverage** | Requirements Tested / Total Requirements | 100% |
| **Test Case Productivity** | Test Cases Executed per Day | Track daily |

### Reporting Frequency

| Report Type | Frequency | Audience |
|-------------|-----------|----------|
| **Daily Status Report** | Daily | QA Lead, PM, Dev Lead |
| **Weekly Summary Report** | Weekly | All Stakeholders |
| **Defect Summary Report** | Weekly | QA Lead, PM, Dev Lead |
| **Test Execution Dashboard** | Real-time (Azure DevOps) | All Stakeholders |
| **Test Closure Report** | End of Testing | All Stakeholders, Management |

### Report Contents
- Test execution summary (pass/fail/blocked/not executed)
- Defect summary by severity and status
- Test coverage metrics
- Risks and issues
- Accomplishments and next steps
- Test evidence (screenshots, calculation sheets)

---

## 17. Communication Plan

### Communication Channels
- **Daily Standup**: 15-min meeting at 9:00 AM with QA, Dev, BA
- **Email Updates**: Daily status sent to stakeholders by EOD
- **Azure DevOps**: Defect tracking and test case updates
- **Microsoft Teams**: Chat channel for quick queries
- **Weekly Review Meeting**: Thursday 2:00 PM - 1 hour with all stakeholders

### Escalation Path
1. **Level 1**: QA Engineer → QA Lead (for test execution issues)
2. **Level 2**: QA Lead → Project Manager (for resource/timeline issues)
3. **Level 3**: Project Manager → Project Sponsor (for critical decisions)

### Contact Information
| Role | Name | Email | Phone |
|------|------|-------|-------|
| QA Engineer | Kishan Thapa | kishan.thapa@company.com | XXX-XXX-XXXX |
| QA Lead | [Name] | [email] | XXX-XXX-XXXX |
| Project Manager | [Name] | [email] | XXX-XXX-XXXX |

---

## 18. Approval

This Test Plan is submitted for approval by the following stakeholders:

| Role | Name | Signature | Date | Status |
|------|------|-----------|------|--------|
| **QA Lead** | [Name] | _________________ | YYYY/MM/DD | Approved / Pending |
| **Project Manager** | [Name] | _________________ | YYYY/MM/DD | Approved / Pending |
| **Business Analyst** | [Name] | _________________ | YYYY/MM/DD | Reviewed |
| **Development Lead** | [Name] | _________________ | YYYY/MM/DD | Reviewed |

---

## Appendices

### Appendix A: Glossary
- **PAYE**: Pay As You Earn (UK tax system)
- **NI**: National Insurance
- **HMRC**: Her Majesty's Revenue and Customs
- **CRM**: Customer Relationship Management (Dynamics CRM)
- **UAT**: User Acceptance Testing
- **Dataverse**: Microsoft Dataverse (cloud database)

### Appendix B: References
- HMRC PAYE Tax Rates 2024/2025
- National Insurance Contribution Rates 2024/2025
- UK Pension Auto-Enrolment Guidelines
- Student Loan Repayment Thresholds 2024/2025
- Project Requirements Document v[X.X]
- System Design Document v[X.X]

### Appendix C: Related Documents
- Test Scenario Document
- Test Case Specifications
- Requirements Traceability Matrix
- API Documentation
- Database Schema

---
