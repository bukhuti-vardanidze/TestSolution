**Software Requirements Specification (SRS) Document**

**Online Ticket Selling Platform**

**Table of Contents**
1. [Introduction](#introduction)
2. [Requirements Gathering](#requirements-gathering)
   - 2.1 [Functional Requirements](#functional-requirements)
   - 2.2 [Non-Functional Requirements](#non-functional-requirements)
3. [System Models](#system-models)
   - 3.1 [Use Case Diagram](#use-case-diagram)
   - 3.2 [Class Diagram](#class-diagram)
   - 3.3 [Sequence Diagram](#sequence-diagram)
   - 3.4 [Activity Diagram](#activity-diagram)
   - 3.5 [State Diagram](#state-diagram)
4. [Glossary](#glossary)

## <a name="introduction"> 1. Introduction </a>

**Purpose:**
The purpose of the online ticket selling platform is to provide a user-friendly and efficient system for buying and selling tickets for various events, including concerts, theater performances, sports events, and movies. The platform aims to simplify the process of ticket transactions, making it accessible to both event organizers and customers.

**Scope:**
The scope of the platform includes functionalities such as event listing, ticket purchasing, payment processing, user registration, and profile management. It will support multiple types of events and provide various payment options to users.

**Objectives:**
- To streamline the ticket buying and selling process.
- To provide a secure and efficient platform for both event organizers and customers.
- To offer a wide range of events and ticket options.
- To enhance user experience through intuitive interfaces and features.

**Intended Users:**
The platform is intended for the following users:
- Event Organizers: Individuals or organizations hosting events who wish to list and sell tickets.
- Customers: Individuals interested in purchasing tickets for various events.

**Assumptions and Dependencies:**
- Assumption 1: Users have access to a stable internet connection.
- Assumption 2: Payment gateways and external APIs for event listings are available and functional.
- Dependency 1: Integration with payment gateways for processing transactions.
- Dependency 2: Integration with external APIs for retrieving event listings and details.

## <a name="requirements-gathering"> 2. Requirements Gathering </a>

**<a name="functional-requirements"> Functional Requirements: </a>**
1. User Registration:
   - Users should be able to create accounts by providing necessary information.
   - Account activation via email verification should be implemented for security purposes.

2. Event Listing:
   - Event organizers should be able to list their events by providing event details such as name, date, venue, and ticket availability.
   - Events should be categorized based on types (concerts, theater, sports, movies, etc.).

3. Ticket Purchasing:
   - Customers should be able to browse through listed events and purchase tickets.
   - Different ticket types (e.g., VIP, regular) should be available for selection.
   - Quantity selection and seat reservation (if applicable) should be supported.

4. Payment Processing:
   - The platform should support various payment methods such as credit/debit cards, digital wallets, and online banking.
   - Payment processing should be secure and PCI-compliant.

5. User Notifications:
   - Users should receive notifications for account activities (e.g., registration confirmation, ticket purchase confirmation).
   - Event organizers should receive notifications for ticket sales and event updates.

**<a name="non-functional-requirements"> Non-Functional Requirements: </a>**
1. Performance:
   - The platform should handle concurrent user requests efficiently to prevent system overload.
   - Response times for actions like page loading and transaction processing should be minimal.

2. Security:
   - User data should be encrypted and stored securely.
   - Secure authentication and authorization mechanisms should be implemented.
   - Payment transactions should be encrypted and comply with PCI-DSS standards.

3. Usability:
   - The user interface should be intuitive and user-friendly.
   - Accessibility features should be implemented to cater to users with disabilities.

4. Compatibility:
   - The platform should be compatible with modern web browsers and mobile devices.
   - Cross-browser and cross-device compatibility testing should be conducted.

**<a name="system-models"> 3. System Models </a>**

### <a name="use-case-diagram">Use Case Diagram </a>
```mermaid
graph TD;
  A[User] -->|Registers| B((System));
  A -->|Browses events| B;
  A -->|Purchases tickets| B;
  B -->|Lists events| C[Event Organizer];
  C -->|Manages events| B;
```


###  <a name="class-diagram"> Class Diagram </a>
```mermaid
classDiagram
  User <|-- Customer
  User <|-- EventOrganizer
  class User {
    -userId: int
    -username: string
    -email: string
    +register()
    +login()
  }
  class Customer {
    -paymentInfo: string
    +purchaseTicket()
    +viewEvents()
  }
  class EventOrganizer {
    -eventsList: array
    +createEvent()
    +manageEvent()
  }
```

**Sequence Diagram:**

### <a name="sequence-diagram"> Sequence Diagram: User Registration </a>
```mermaid
sequenceDiagram
  participant User
  participant System
  User ->> System: Request to register
  System ->> User: Provide registration form
  User ->> System: Fill out registration form
  System ->> System: Validate registration data
  alt Registration data valid
    System ->> User: Registration successful
  else Registration data invalid
    System ->> User: Error message with invalid fields
  end
```

### <a name="activity-diagram"> Activity Diagram: Ticket Purchasing Process </a>
```mermaid
graph TD;
  A[Start] --> B{Ticket Selection};
  B -->|Select Ticket| C{More Tickets?};
  C -->|Yes| B;
  C -->|No| D[Proceed to Payment];
  D --> E[Payment];
  E --> F[Confirmation];
  F --> G[End];
```

### <a name="state-diagram"> State Diagram: Ticket Lifecycle </a>
```mermaid
stateDiagram-v2
  [*] --> Available
  Available --> Reserved
  Reserved --> Sold
  Reserved --> Canceled
  Sold --> [*]
  Canceled --> [*]
```

4. **<a name="glossary">Glossary:</a>** 

- **User:** An individual who interacts with the platform, either as an event organizer or a customer.
- **Event Organizer:** A user who lists and manages events on the platform.
- **Customer:** A user who purchases tickets for events listed on the platform.
- **PCI-DSS:** Payment Card Industry Data Security Standard, a set of security standards designed to ensure that all companies that accept, process, store, or transmit credit card information maintain a secure environment.
- **API:** Application Programming Interface, a set of rules and protocols for building and interacting with software applications.
- **Conclusion:** This Software Requirements Specification document outlines the requirements and system models for the development of an online ticket selling platform. By adhering to these specifications, the platform aims to provide a seamless experience for both event organizers and customers while ensuring security, efficiency, and user satisfaction.

```


