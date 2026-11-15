# Remote Team Time-Tracking & Project Approver

## 📌 Project Overview

The **Remote Team Time-Tracking & Project Approver** is an engineering productivity system designed to help remote development teams record working hours against Jira or project tasks, submit timesheets for managerial approval, and monitor project budget usage.

The system provides a structured workflow between **Remote Developers** and **Engineering Managers**. Developers record and submit their working hours, while managers review, approve or reject submitted timesheets and monitor project budget usage.

This project was developed as part of **Lab 1: Requirements Engineering & UML Use-Case Modelling**.

---

## 🎯 Problem Statement

Remote development teams need an efficient way to track the amount of time developers spend on project tasks while ensuring that recorded hours are properly reviewed and approved.

Without a structured time-tracking and approval process:

- Working hours may be recorded inaccurately.
- Managers may have difficulty verifying submitted hours.
- Project budget usage may not be visible.
- Unauthorized users may access restricted timesheet information.
- Invalid or incomplete timesheets may be submitted.

The proposed system addresses these issues by providing time logging, timesheet submission and validation, managerial approval, rejection, and project budget monitoring.

---

## 👥 Actors

The system contains two primary actors.

### 1. Remote Developer

The Remote Developer is responsible for:

- Viewing Jira/project tasks.
- Logging working hours against a task.
- Submitting completed timesheets.
- Correcting invalid timesheet information when validation fails.

### 2. Engineering Manager

The Engineering Manager is responsible for:

- Reviewing submitted timesheets.
- Approving valid timesheets.
- Rejecting timesheets with a reason.
- Monitoring project budget usage based on recorded developer hours.

---

## 🔑 Main Use Cases

The major use cases identified for the system are:

| Use Case | Description |
|---|---|
| **View Jira Tasks** | Allows the Remote Developer to view the required Jira/project tasks. |
| **Log Work Hours** | Allows the developer to record working hours against a specific task. |
| **Submit Timesheet** | Allows the developer to submit a completed timesheet for approval. |
| **Validate Timesheet** | Validates the information entered in the timesheet before submission. |
| **Review Timesheet** | Allows the Engineering Manager to review submitted working hours and task details. |
| **Approve Timesheet** | Allows the Engineering Manager to approve a valid submitted timesheet. |
| **Reject Timesheet** | Allows the Engineering Manager to reject a submitted timesheet with a reason. |
| **Monitor Project Budget** | Allows the Engineering Manager to monitor project hours and budget usage. |

---

## 🏗️ System Boundary

The UML use-case model defines the system boundary as the **Remote Team Time-Tracking & Project Approver** system.

The actors interact with the system through the following major functions:

```text
Remote Developer
      |
      +--> View Jira Tasks
      |
      +--> Log Work Hours
      |
      +--> Submit Timesheet
                |
                +--> <<include>>
                     Validate Timesheet


Engineering Manager
      |
      +--> Review Timesheet
      |
      +--> Approve Timesheet
      |
      +--> Reject Timesheet
      |
      +--> Monitor Project Budget
```

The UML diagram identifies the actors as **Remote Developer** and **Engineering Manager**, with `<<include>>` and `<<extend>>` relationships between the relevant use cases.

---

# 📋 Requirements

## Functional Requirements

### FR-001: Log Working Hours

The system shall allow a **Remote Developer** to log working hours against a specific Jira/project task.

**Priority:** High

**Acceptance Criteria:**

- Pass: A developer can enter a valid Jira task and working hours and save the entry.
- Fail: The system rejects the entry when the task or working hours are invalid or missing.

**Rationale:**  
To accurately track time spent by developers on project tasks.

---

### FR-002: Submit Timesheet

The system shall allow a **Remote Developer** to submit a completed timesheet to the **Engineering Manager** for approval.

**Priority:** High

**Acceptance Criteria:**

- Pass: A completed timesheet can be submitted successfully.
- Fail: Submission is prevented when required information is missing.

**Rationale:**  
To send recorded working hours to the manager for review.

---

### FR-003: Review Timesheet

The system shall allow an **Engineering Manager** to review submitted timesheets.

**Priority:** High

**Acceptance Criteria:**

- Pass: The manager can view submitted hours and task details.
- Fail: An unsubmitted timesheet cannot be reviewed.

**Rationale:**  
To allow the manager to verify recorded working hours.

---

### FR-004: Approve or Reject Timesheet

The system shall allow an **Engineering Manager** to approve or reject a submitted timesheet.

**Priority:** High

**Acceptance Criteria:**

- Pass: The manager can approve a valid timesheet or reject it with a reason.
- Fail: An unsubmitted timesheet cannot be approved or rejected.

**Rationale:**  
To provide managerial control over recorded project hours.

---

### FR-005: Monitor Project Budget

The system shall allow an **Engineering Manager** to monitor project budget usage based on recorded developer hours.

**Priority:** Medium

**Acceptance Criteria:**

- Pass: The manager can view project hours and budget usage.
- Fail: Budget information is not displayed when required project data is unavailable.

**Rationale:**  
To help managers monitor project spending and avoid budget overruns.

---

## Non-Functional Requirements

### NFR-001: Performance

Timesheet approval status and project budget charts shall update across dashboards within **500 ms**.

**Priority:** High

**Acceptance Criteria:**

- Pass: Benchmarking confirms dashboard updates within 500 ms under simulated peak load.
- Fail: Updates consistently take more than 500 ms.

**Rationale:**  
To provide fast and responsive project monitoring.

---

### NFR-002: Security

The system shall ensure that:

- Remote Developers can access only their own timesheets.
- Engineering Managers can access timesheets and budget information for their assigned projects.
- Unauthorized users are denied access.

**Priority:** High

**Acceptance Criteria:**

- Pass: Unauthorized users are denied access.
- Fail: A developer can access another developer's restricted information.

**Rationale:**  
To protect timesheet and project budget information.

The complete requirements table defines FR-001 through FR-005 and NFR-001 through NFR-002 with their priorities, acceptance criteria, and rationale.

---

# 🔄 Use-Case Relationships

The UML model uses the following relationships.

## `<<include>>`

The **Submit Timesheet** use case includes **Validate Timesheet**.

```text
Submit Timesheet
       |
       | <<include>>
       v
Validate Timesheet
```

This means that validation is a required part of the timesheet submission process.

Before a timesheet can be successfully submitted, the system validates the entered information.

---

## `<<extend>>`

The timesheet review process is extended by the approval and rejection actions.

```text
              +--> Approve Timesheet
              |
Review Timesheet
              |
              +--> Reject Timesheet
```

The UML diagram represents **Approve Timesheet** and **Reject Timesheet** as `<<extend>>` relationships associated with the review process.

---

# 📝 Use-Case Specification: UC-002

## Use Case: Submit Timesheet

**Use Case ID:** UC-002

**Primary Actor:** Remote Developer

**Goal:**  
To submit the developer's recorded working hours for Engineering Manager approval.

---

## Preconditions

The following conditions must be satisfied before submitting a timesheet:

1. The Remote Developer is logged into the system.
2. The developer has access to the required project or Jira task.
3. The developer has entered the required working hours.
4. The timesheet contains the required information.

These preconditions are defined in the submitted use-case flow specification.

---

## Main Success Scenario

The successful submission process follows these steps:

1. The Remote Developer logs into the system.
2. The developer opens the timesheet section.
3. The developer selects the required project or Jira task.
4. The developer enters the working hours.
5. The developer selects **Submit Timesheet**.
6. The system validates the entered timesheet information.
7. The system confirms that the timesheet information is valid.
8. The system submits the timesheet.
9. The system changes the timesheet status to **Pending Approval**.
10. The system makes the submitted timesheet available to the Engineering Manager for review.
11. The system displays a successful submission message to the developer.

The detailed flow specification defines these 11 steps for UC-002.

---

## Alternative Flow: Invalid Timesheet Information

If the timesheet contains incomplete or invalid information:

1. The Remote Developer enters incomplete or invalid timesheet information.
2. The developer selects **Submit Timesheet**.
3. The system validates the timesheet.
4. The system detects the invalid or missing information.
5. The system displays an error message to the developer.
6. The system does not submit the timesheet.
7. The developer corrects the information.
8. The developer submits the timesheet again.
9. The system validates and processes the corrected timesheet.

This ensures that invalid information does not enter the approval workflow.

---

## Postconditions

### Successful Submission

After a successful submission:

- The timesheet is successfully submitted.
- The timesheet status changes to **Pending Approval**.
- The Engineering Manager can review the submitted timesheet.

### Failed Submission

If submission fails:

- The timesheet is not submitted.
- The entered information remains available for correction.
- The developer is informed about the validation error.



---

# 🔁 Overall System Workflow

The overall workflow of the system can be represented as:

```text
                 REMOTE DEVELOPER
                        |
                        v
                View Jira Tasks
                        |
                        v
                 Log Work Hours
                        |
                        v
                Submit Timesheet
                        |
                        v
               Validate Timesheet
                    /       \
                   /         \
              Invalid         Valid
                 |              |
                 v              v
          Display Error     Submit Timesheet
                 |              |
                 |              v
                 |        Pending Approval
                 |              |
                 |              v
                 |       Engineering Manager
                 |              |
                 |              v
                 |       Review Timesheet
                 |          /       \
                 |         /         \
                 |        v           v
                 |   Approve       Reject
                 |   Timesheet     Timesheet
                 |                    |
                 |                    v
                 |              Rejection Reason
                 |
                 +----> Correct Information
                              |
                              v
                        Submit Again
```

---

# 📊 Project Budget Monitoring

The system also supports project budget monitoring.

The Engineering Manager can monitor:

- Recorded developer hours.
- Project hours.
- Budget usage.

The purpose of this functionality is to help managers monitor project spending and avoid budget overruns.

This functionality is represented by the **Monitor Project Budget** use case and is defined as FR-005 in the requirements table.

---

# 🔐 Security

Security is an important non-functional requirement of the system.

The system must ensure that:

```text
Remote Developer
      |
      +--> Own Timesheets Only

Engineering Manager
      |
      +--> Timesheets for Assigned Projects
      |
      +--> Budget Information for Assigned Projects
```

Unauthorized users must be denied access to restricted timesheet and project budget information.

This requirement is defined under **NFR-002**.

---

# ⚡ Performance

The system specifies a performance requirement for dashboard updates.

### Target

**Dashboard update time: ≤ 500 ms**

This applies to:

- Timesheet approval status.
- Project budget charts.

The requirement is intended to provide fast and responsive project monitoring.

---

# 📁 Repository Structure

The project repository contains the following structure:

```text
Remote-Team-Time-Tracking-Project/
│
├── README.md
│
├── requirements/
│   └── requirements_table.md
│
├── use-case-flow/
│   └── submit_timesheet.md
│
└── use-case-diagram/
    └── use_case_diagram.png
```

### `README.md`

Contains the project overview, actors, deliverables, and major use cases.

### `requirements/requirements_table.md`

Contains the complete functional and non-functional requirements, including:

- FR-001
- FR-002
- FR-003
- FR-004
- FR-005
- NFR-001
- NFR-002

### `use-case-flow/submit_timesheet.md`

Contains the detailed specification for **UC-002: Submit Timesheet**, including:

- Primary actor
- Goal
- Preconditions
- Postconditions
- Main success scenario
- Alternative flow
- Result

### `use-case-diagram/use_case_diagram.png`

Contains the UML use-case diagram showing the system boundary, actors, use cases, and `<<include>>` / `<<extend>>` relationships.

---

# 📦 Project Deliverables

The project provides the following deliverables:

### 1. Requirements Table

A complete requirements table containing:

- Functional requirements FR-001 to FR-005.
- Non-functional requirements NFR-001 to NFR-002.
- Priorities.
- Acceptance criteria.
- Rationale.

### 2. UML Use-Case Diagram

The UML diagram represents:

- Remote Developer.
- Engineering Manager.
- Primary system use cases.
- `<<include>>` relationship.
- `<<extend>>` relationships.
- System boundary.

### 3. Use-Case Flow Specification

A detailed use-case specification for:

**UC-002: Submit Timesheet**

The specification includes both the successful and invalid-input scenarios.

---

# 📚 Academic Context

**Lab:** Lab 1: Requirements Engineering & UML Use-Case Modelling

**Project:** Remote Team Time-Tracking & Project Approver

**Primary Actors:**

- Remote Developer
- Engineering Manager

**Key Modelling Concepts:**

- Functional Requirements
- Non-Functional Requirements
- UML Use-Case Modelling
- System Boundary
- Actors
- `<<include>>`
- `<<extend>>`
- Use-Case Flow Specification
- Preconditions
- Postconditions
- Main Success Scenario
- Alternative Flow
- Acceptance Criteria

---

# ✅ Requirement Traceability

| Requirement | Related Use Case |
|---|---|
| FR-001 | Log Work Hours |
| FR-002 | Submit Timesheet |
| FR-003 | Review Timesheet |
| FR-004 | Approve Timesheet / Reject Timesheet |
| FR-005 | Monitor Project Budget |
| NFR-001 | Dashboard / Budget Monitoring |
| NFR-002 | All restricted timesheet and budget operations |

---

# 🎓 Conclusion

The **Remote Team Time-Tracking & Project Approver** provides a structured model for managing developer work hours and project approval workflows.

The system enables Remote Developers to record and submit their working hours against Jira/project tasks, while Engineering Managers can review, approve, reject, and monitor project budget usage.

The requirements, UML use-case model, and detailed **Submit Timesheet** use-case specification together define the expected behavior and constraints of the proposed system.
