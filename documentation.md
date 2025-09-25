# 1-Stop Book Project Documentation

## 1. Introduction

### Background

Provide the background and context of the project and its current status from a project perspective.

In Bhutan, booking services whether for sports fields, healthcare appointments, salons, or tourism still largely rely on traditional methods such as phone calls, in-person visits, or manual coordination. This outdated approach often results in inefficiencies, including miscommunications, double bookings, and delays in service delivery. For instance, the Ministry of Health has acknowledged difficulties in managing patient appointments, emphasizing the need for improved systems to reduce wait times and enhance service efficiency (Dema, 2024).

Similarly, the Bhutan Football Federation (BFF) recently shared information about ground bookings through a social media post, asking people to contact a phone number to make reservations. This method drew public criticism, with many highlighting the urgent need for an online booking system (Bhutan Broadcasting Service, 2020). The tourism sector also faces comparable challenges. Although initiatives like the Tourism Bhutan app have been introduced, users frequently report issues such as crashes, connectivity problems, and unreliable payment systems, which further add to user frustration and operational strain (Reguerra, 2024).

Recognizing these challenges, the **1-Stop Book** project seeks to provide a centralized, user-friendly platform that integrates multiple booking services into a single application. For this semester, the project will begin by developing a ground booking system for our college. In the long term, the scope will expand to include healthcare, salon, restaurant, and tourism bookings, and extend its reach to other colleges and institutions. By consolidating services, the platform aims to enable real-time availability checks, reduce administrative burdens, and improve overall user experience, ultimately supporting Bhutan's digital transformation journey.

## 2. Business Needs/Problem Statement

Include a brief summary of the business needs and drivers for the initiative. (The why of this project, what are you trying to solve?)

The college currently relies on a manual booking process for facilities such as sports grounds, event halls, and recreational spaces, managed through WhatsApp messages and emails. This creates double bookings, scheduling conflicts, long wait times, and poor visibility of real-time availability. Students, faculty, and coordinators have difficulty in tracking reservations without a centralized system, while the lack of proper record-keeping prevents usage reporting or dispute resolution. As the college community grows, this fragmented system becomes increasingly inefficient and unsustainable. Therefore, there is a strong need for a unified digital platform that streamlines bookings, provides real-time availability, reduces administrative workload, and supports scalability for future expansion.

### Key Issues

- Double bookings and scheduling conflicts
- Poor communication and delayed responses
- Heavy administrative burden on staff
- No real-time availability tracking
- Inability to generate usage reports
- Underutilized facilities due to poor visibility
- Lack of proper documentation and record-keeping
- Not scalable for growing college needs

## 3. Stakeholders

List the key business and IT stakeholders in the initiative.

### Business Stakeholders

- Service providers (sports ground owners)
- End customers (users making reservations)  
- Business partners & investors supporting the platform

### IT Stakeholders

- Product Owner & Project Manager
- Software Development Team (Frontend, Backend, Mobile, QA)
- System Architect / Solution Designer
- Operations & DevOps team (deployment, monitoring, scaling)

## 4. Project Scope

Briefly describe the scope of the solution. State what is included in the scope and what is out of scope. If relevant, define the phases of the solution and what is delivered in each phase. Provide references to the documented scope. Also clearly define the scope for the architecture, design and implementations if you do not implement everything that you have architectured.

### In Scope

- Development of the booking platform focusing on football ground bookings as the first implemented service
- User registration and login functionality
- Booking management (view, create, cancel bookings)
- Basic payment integration
- Admin panel for managing bookings and service availability

### Out of Scope

- Implementation of other services such as salons, restaurants, or futsal grounds in the first phase
- Advanced features like dynamic pricing, loyalty points, or AI-based recommendations (can be considered in later phases)
- Complex analytics dashboards for service providers

### Functionality in scope

Briefly list down the requirements that are in the scope of the project.

- User registration, login, and profile management
- Search and view available football grounds
- Create, modify, and cancel bookings
- Payment processing for bookings
- Admin panel for booking and availability management
- Notifications for booking confirmations and reminders

### Functionality out of scope

Briefly list down the requirements that are out of scope of the project.

- Booking for services other than football grounds (in Phase 1)
- Advanced payment options like installment or subscriptions
- Loyalty programs or gamification features
- Analytics or reports for service providers

## 5. Role Division

- **Frontend Developer**: Builds the user interface (UI) and ensures users can interact smoothly with the website
- **Backend Developer with Database**: Handles the server side, APIs, and database. Ensures data is stored, retrieved, and processed correctly
- **DevOps Engineer**: Manages deployment, automation, and CI/CD pipelines
- **Security Engineer**: Focuses on protecting the system from attacks. Handles authentication, authorization, and security best practices
- **Quality Assurance (QA) Engineer**: Tests the app to find bugs, ensure performance, and verify everything works as expected
- **Solution Architect**: Designs the overall structure of the system, deciding how components (frontend, backend, database, etc.) fit together
- **Business Analyst**: Understands user and business needs, documents requirements, and ensures the solution aligns with business goals

## 6. Project Conduct

### Project Plan

Describe the rough WBS tasks and the estimated efforts.

### Project Status

Describe the current status of the project. Highlight if there are outstanding issues/doubts that need to be addressed and researched on.

### Project Metrics

Provide the actual project milestones achieved as well as the rough total effort expended by each team member.

## 7. Solution Overview

The College Ground Booking Application is a centralized, web-based platform designed to manage and streamline the reservation of college grounds and facilities. The solution provides an intuitive interface for students, faculty, and administrative staff to view ground availability, place booking requests, and manage schedules. The primary business objective is to enhance operational efficiency by automating the booking process, eliminating scheduling conflicts, and providing data-driven insights into facility utilization.

The architecture is driven by key quality attributes including scalability to handle peak loads, maintainability for long-term development, robust security to protect user data, and high availability for constant access.

## 8. Logical Architecture & Design

Describe the architecturally significant parts (or elements) of the solution and the design model showing its decomposition into subsystems using logical detail deployment diagram and other diagrams as necessary.

The individual elements of the solution must be clearly defined and assigned to the respective providers. An element (or subset of multiple elements) may be allocated to a Vendor.

A solution element is any part of the architecture of the overall solution, e.g., a COTS product, a custom-built software module, a data repository, a network device, etc. Each element can utilise the services provided by other elements and provide services of its own.

The logical view describes how elements participate in the solution. It includes static and dynamic relationships and interactions between elements. The documentation typically includes a number of diagrams expressing the different kinds of relationships — for example, dependency relationships, usage relationships, interaction relationships, etc.

The logical architecture of the solution adopts a microservices approach, decomposing the system into a collection of independently deployable services organized around business capabilities. This modular design promotes a clear separation of concerns, enhances fault isolation, and supports the architectural driver of maintainability. Communication between services is managed via a central API Gateway for synchronous requests and an event bus for asynchronous communication.

### Key Architectural Decisions

Provide a summary of the significant decisions made in arriving at the architecture of the solution that are related and/or reflected in the logical view. Documented decisions should focus on trade-off choices and rationale.

The key architectural decisions taken are as follows:

| Identifier | Description |
|------------|-------------|
| **AD-01** | **Microservices Architecture**: The solution is decomposed into small, independent services based on business capabilities (e.g., User Service, Booking Service). **Rationale**: This directly supports the drivers of Maintainability and Scalability. It allows small, focused teams to develop and deploy services independently. While a monolithic architecture offers lower initial complexity, this approach was chosen to prevent the creation of a tightly-coupled system that is difficult to change over the long term. **Trade-off**: Increased operational complexity in deployment, monitoring, and inter-service communication. |
| **AD-02** | **API Gateway Pattern**: All client requests from the frontend application are routed through a single, managed API Gateway. **Rationale**: This centralizes cross-cutting concerns like authentication, security (rate limiting), and logging, simplifying the individual microservices and enforcing consistent policies. This supports the Security driver. **Trade-off**: The gateway can become a single point of failure if not configured for high availability and can introduce a slight latency overhead. |

### Tiers and Layers

Describe the tiers and layers of the solution. E.g. Presentation layer, Business Logic layer, Data Access layer, Web Server tier and Integration tier. Adapt the section if you organized the solution using a different method (not tiered or layered approach).

The solution is organized into a classic multi-tier architecture:

- **Presentation Tier**: The client-side Single-Page Application (SPA) running in the user's browser. It is responsible for all rendering and user interaction.
- **Application/Business Tier**: The backend, composed of the stateless microservices and the API Gateway. Each microservice internally contains its own layers for controllers (API exposure), business logic (services), and data access (repositories).
- **Persistence Tier**: The managed relational database system that stores all application state and serves as the single source of truth.

### Nodes and Subsystems

Describe the architecturally significant parts (or elements) of the solution showing the decomposition into subsystems.

The logical decomposition of the solution consists of the following subsystems, which function as logical nodes in the architecture:

- **Frontend Web Application**: The user-facing subsystem providing the graphical interface
- **User Service**: The subsystem responsible for identity and access management
- **Grounds Service**: The subsystem that manages the master data for all bookable grounds and facilities
- **Booking Service**: The core transactional subsystem that manages the lifecycle of reservations
- **Approval Workflow Service**: A dedicated subsystem to manage the business logic for booking approvals
- **Notification Service**: A centralized subsystem for dispatching all user communications

### Platform Design

Where relevant, describe the elements of Domain Driven Design like domain entities, bounded contexts, aggregates, domain events, etc. In particular, describe how the platform is designed to interact with the producers and consumers.

## 9. Physical Architecture & Design

Describe the architecturally significant components (or elements) of the solution by describing the physical design which may include the network, technologies, nodes and machines where the components are deployed using physical detail deployment and other diagram as necessary. This is where you can also include and describe the cloud services that you use if any.

### Physical Architecture Key Decisions

Provide a summary of the significant decisions made in arriving at the architecture of the solution that are related and/or reflected in the physical view. Documented decisions should focus on trade-off choices and rationale. You should continue the numbering from the previous architectural decisions table.

The key architectural decisions taken are as follows:

| Identifier | Description |
|------------|-------------|
| **AD-03** | ... |
| **AD-04** | ... |
