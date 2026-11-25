# Software Requirements — InAndOut

## 1. Purpose

InAndOut is a multi-tenant logistics platform that connects transport companies and terminals to streamline transport bookings, container handling, fleet management, and gate operations.

## 2. Actors

| Actor | Responsibility |
|---|---|
| System Administrator | Manages the platform, organizations and registration requests. |
| Company Administrator | Manages company employees and vehicles. |
| Transport Manager | Creates bookings and assigns drivers and trucks. |
| Driver | Views assigned bookings and their status. |
| Terminal Administrator | Manages terminal employees and resources. |
| Gate Operator | Handles truck check-in and check-out. |
| Yard Operator | Handles container loading and unloading. |
| Demo Visitor | Explores the platform using isolated demo data. |

## 3. Functional Requirements

| ID | Requirement |
|---|---|
| FR-01 | The system shall authenticate users and enforce role-based access control. |
| FR-02 | The system shall support multiple transport companies and terminals. |
| FR-03 | Administrators shall manage employees within their organization. |
| FR-04 | Company employees with appropriate permissions shall manage trucks and drivers. |
| FR-05 | Terminal employees with appropriate permissions shall manage containers and yard slots. |
| FR-06 | Transport managers shall create, view and cancel eligible bookings. |
| FR-07 | Transport managers shall assign drivers and trucks to bookings. |
| FR-08 | Drivers shall view their assigned bookings. |
| FR-09 | Gate operators shall check trucks in and out. |
| FR-10 | Yard operators shall manage container loading and unloading. |
| FR-11 | The system shall track booking status throughout its lifecycle. |
| FR-12 | The system shall record operational events and audit logs. |
| FR-13 | The system shall provide role-specific dashboards. |
| FR-14 | Visitors shall be able to access an isolated interactive demo. |

## 4. Non-Functional Requirements

| ID | Requirement |
|---|---|
| NFR-01 | Security: Passwords shall be hashed, and communication shall use HTTPS in production. |
| NFR-02 | Data isolation: Organizations shall not access unauthorized data belonging to other organizations. |
| NFR-03 | Maintainability: The system shall follow a modular, layered architecture. |
| NFR-04 | Testability: Critical business rules shall be covered by automated tests. |
| NFR-05 | Usability: The interface shall be responsive and role-specific. |
| NFR-06 | Data integrity: The system shall prevent conflicting assignments and invalid state transitions. |
| NFR-07 | Deployment: The application shall support containerized deployment and automated CI/CD. |
| NFR-08 | Demo isolation: Demo users shall not access production data or other visitors' demo data. |

## 5. Business Rules

- BR-01: Every user must have an authorized role.
- BR-02: Company and terminal employees must belong to their respective organizations.
- BR-03: Every booking must reference a company, terminal, driver, truck and container.
- BR-04: The assigned driver and truck must belong to the booking's transport company.
- BR-05: A truck cannot have conflicting active bookings.
- BR-06: A yard slot cannot contain more than one container.
- BR-07: A truck must check in before container handling begins.
- BR-08: Container handling must be completed before truck check-out.
- BR-09: Only scheduled bookings may be cancelled in the MVP.
- BR-10: All booking status transitions must be validated by the backend.
- BR-11: Operational events must record the responsible user and timestamp.

## 6. Booking Lifecycle

SCHEDULED → CHECKED_IN → IN_PROGRESS → READY_FOR_EXIT → COMPLETED

A scheduled booking may alternatively transition to CANCELLED.

## 7. Future Enhancements

- Public customer registration and approval
- Email invitations
- Real-time notifications
- Advanced reporting and analytics
- GPS fleet tracking
- External logistics integrations
- Kubernetes deployment
