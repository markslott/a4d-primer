# Time Clock Application Requirements (Salesforce)

These requirements outline the necessary features and data structure for a simple employee time-tracking application built within the Salesforce Lightning Platform.

## 1. User Experience (UX/UI) Requirements

The design philosophy must prioritize simplicity and accessibility for non-technical users.

| ID | Requirement | Description | Priority |
| ---- | ----------- | ----------- | -------- |
| **UX-100** | **Single-Button Interaction** | The primary component must display only **one** large, clearly labeled, interactive button at any given time: either "Clock In" or "Clock Out." The button should be square and approximately 2 inches wide on the display | High |
| **UX-101** | **Clear Status Display** | A prominent, real-time message must clearly indicate the user's current status (e.g., "**Currently Clocked In** since 9:00 AM" or "**Currently Clocked Out**"). | High |
| **UX-102** | **Visual Feedback (Color)** | Use an intuitive color scheme: **Green** for "Clock In" and a positive "Clocked In" status, and **Red** for "Clock Out" and a neutral "Clocked Out" status. | High |
| **UX-103** | **Responsive Design** | The component must be fully responsive and optimized for use on both desktop (Lightning App Builder) and mobile devices (Salesforce App). | High |
| **UX-104** | **No Manual Time Entry** | Employees must **not** be able to manually edit the clock-in or clock-out times. All times must be recorded automatically upon button click. | High |
| **UX-105** | **Display Errors** | Any errors need to be reported back to the user in a clear and user-friendly manner. | High |

## 2. Functional Requirements

These define how the application must behave when a user interacts with it.

| ID | Requirement | Description | Priority |
| ---- | ----------- | ----------- | -------- |
| **FUN-200** | **Clock In Action** | Upon clicking the "Clock In" button, the system must create a new Time Entry record, recording the current date and time as the **Start Time**. | High |
| **FUN-201** | **Clock Out Action** | Upon clicking the "Clock Out" button, the system must find the active Time Entry record, record the current date/time as the **End Time**, and trigger server-side **Apex** to calculate and populate the **Duration** and **Work Week** fields. | High |
| **FUN-202** | **Prevent Double Clock-In** | If a user is currently clocked in (has an active Time Entry record without an End Time), the system must prevent them from clocking in again. | High |
| **FUN-203** | **User Identification** | All Time Entry records must automatically link to the logged-in Salesforce **User** who performed the action. | High |
| **FUN-204** | **Time Zone Handling** | All recorded times must be stored as **Coordinated Universal Time (UTC)** and displayed to the user based on their individual Salesforce **User Time Zone settings**. | High |
| **FUN-205** | **Audit Trail** | All clock-in and clock-out actions must be logged with timestamps and user information for audit purposes. | Medium |

## 3. Data Model Requirements

The application will require one custom object to store the time entries.

| ID | Specification | Details | Priority |
| ---- | ----------- | ----------- | -------- |
| **DATA-300** | **Custom Object** | Create a Custom Object: `Time_Card__c` | High |
| **DATA-302** | **Field: Start Time** | Data type: **Date/Time** (`Start_Time__c`). Automatically set on "Clock In." | High |
| **DATA-303** | **Field: End Time** | Data type: **Date/Time** (`End_Time__c`). Automatically set on "Clock Out." | High |
| **DATA-304** | **Field: Duration** | Data type: **Number** (`Duration__c`). The duration (in hours, decimal format) must be calculated via **Apex** upon clock-out. | High |
| **DATA-305** | **Field: Work Week** | Data type: **Text** (`Work_Week__c`). The week grouping (e.g., `YYYY-WW`) must be calculated via **Apex** upon clock-in and/or clock-out. | Medium |
| **DATA-306** | **Field: Created By** | Data type: **Lookup** to User (`Created_By__c`). Automatically populated with the current user. | High |
| **DATA-307** | **Field: Status** | Data type: **Picklist** (`Status__c`). Values: "Active", "Completed", "Cancelled". | Medium |

## 4. Reporting Requirements

The system must support simple and accurate reporting for payroll and management review.

| ID | Requirement | Description | Priority |
| ---- | ----------- | ----------- | -------- |
| **REP-400** | **Weekly Hours Summary Report** | A standard Salesforce report that allows managers to view the total number of hours worked by each employee, **grouped by week**. | High |
| **REP-401** | **Time Entry Detail Report** | A standard Salesforce report showing every clock-in and clock-out event for auditing purposes, including the date, start time, end time, and duration. | Medium |
| **REP-402** | **Filtering by Week/Month** | All reports must allow easy filtering by date range, specifically focused on filtering by **Work Week** (using the calculated field from DATA-305). | High |
| **REP-403** | **Individual Employee Report** | A report allowing employees to view their own time entries and hours worked over a specified period. | Medium |

## 5. Technical Stack Requirements

These define the specific framework required for implementation.

| ID | Requirement | Description | Priority |
| ---- | ----------- | ----------- | -------- |
| **TECH-500** | **Component Technology** | The primary clock-in/clock-out UI must be implemented as a **Lightning Web Component (LWC)**. | High |
| **TECH-501** | **Apex Controller** | Server-side logic must be implemented in an **Apex Class** to handle time calculations and data persistence. | High |
| **TECH-502** | **Error Handling** | All components must include proper error handling and user feedback mechanisms. | High |
| **TECH-503** | **Security** | All Apex code must follow Salesforce security best practices including SOQL injection prevention and proper sharing rules. | High |

## 6. Additional Requirements

| ID | Requirement | Description | Priority |
| ---- | ----------- | ----------- | -------- |
| **ADD-600** | **Performance** | The application must respond within 2 seconds for all user interactions. | Medium |
| **ADD-601** | **Accessibility** | The component must comply with WCAG 2.1 AA accessibility standards. | High |
| **ADD-602** | **Testing** | All Apex classes must have unit tests with 75%+ code coverage. | High |
| **ADD-603** | **Documentation** | Provide inline documentation for all Apex methods and LWC components. | Medium |
