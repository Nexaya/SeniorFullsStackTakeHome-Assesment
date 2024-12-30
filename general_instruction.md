# Take-Home Assessment: Senior FullStack Engineer
### **Please Ensure To Read All Instructions**
## Scenario

### Problem Context
You are building an AI-Assisted Marketplace for Freelancers with capabilities for project matching, bidding, and analytics. The platform will enable clients to post projects, freelancers to bid on those projects, and an AI engine to recommend the best matches based on skills, ratings, and historical performance. Additionally, the system must handle real-time notifications, payment handling, and complex analytics for clients and freelancers.

This problem introduces a real-world mix of business rules, architectural challenges, and multi-user workflows to ensure originality and encourage innovative problem-solving.

---

## Assessment Description
Develop a scalable and robust web application backend that powers the marketplace. The task will cover designing APIs, data models, and architectural decisions while also providing a basic UI to consume these APIs. The project includes significant constraints and functional complexity to evaluate in-depth problem-solving and system design skills.

---

## Requirements

### Functional Requirements

#### User Management
- Freelancers and clients can register and log in.
- Role-based access (client or freelancer).
- Profile management for freelancers (skills, bio, portfolio).

#### Project Management
- Clients can post projects with requirements (title, description, budget range, skills required, deadline).
- Freelancers can browse and search projects.
- Freelancers can submit bids for projects (bid amount, estimated delivery time, proposal text).
- Clients can view and accept/reject bids.

#### AI Recommendation Engine
- Match projects to freelancers based on:
  - Skills overlap.
  - Freelancer ratings.
  - Historical completion rates.
- Recommendations should improve over time using a simulated dataset.

#### Payments
- Secure payment handling (e.g., Stripe or mock integration).
- Clients pay upon accepting a bid. Funds are held in escrow until project completion.
- Freelancers receive payments after client approval.

#### Real-Time Notifications
- Notify freelancers of new projects that match their skills.
- Notify clients when bids are submitted or updated.

#### Analytics Dashboard
- Freelancers can view:
  - Total earnings.
  - Projects completed.
  - Average ratings over time.
- Clients can view:
  - Money spent on projects.
  - Average completion time.
  - Freelancer performance.

---

### Non-Functional Requirements

#### Scalability
- Support 100,000+ active users with real-time interactions.
- Handle simultaneous bidding on projects and notifications efficiently.

#### Performance
- API response time ≤ 150ms for 90% of requests.
- Minimal latency for real-time notifications.

#### Security
- Secure all APIs using JWT authentication.
- Encrypt sensitive data (e.g., passwords using bcrypt).
- Prevent vulnerabilities like SQL injection, CSRF, and XSS.

#### Reliability
- Gracefully handle network errors, database timeouts, and payment failures.
- Implement retries for time-sensitive operations.

#### Maintainability
- Modular, testable, and easily extensible architecture.
- Clear documentation for APIs, data models, and business rules.

---

## Deliverables

1. **Code**
   - Full-stack implementation:
     - Backend with APIs and necessary business logic.
     - Basic frontend UI to demonstrate API functionality.

2. **Tests**
   - Unit tests for core logic and components.
   - Integration tests for key workflows (e.g., project bidding, payments).
   - Performance/load testing scripts (simulate real-world scenarios).

3. **Documentation**
   - `README.md`:
     - Project setup instructions.
     - Explanation of architecture, trade-offs, and known limitations.
     - API documentation (Swagger/OpenAPI).
     - Database schema with ER diagrams.

---

## Constraints

### Technology Stack
- **Backend**: Python (FastAPI), Node.js (Nest.js), or Java (Spring Boot).
- **Database**: PostgreSQL (preferred), MongoDB (optional for flexibility).
- **Frontend**: React.
- **Queueing**: RabbitMQ, Kafka, or Redis for notifications and AI tasks.
- **Search**: Elasticsearch for complex project searches(optional).

### Architectural Patterns
- Microservice or modular monolith design.
- Event-driven architecture for real-time features.

---

## Performance Benchmarks
- Scale to handle 1,000+ simultaneous projects and 10,000+ real-time notifications.

---

## Evaluation Criteria

1. **Code Quality**
   - Clean, maintainable, and testable code adhering to best practices.

2. **Scalability**
   - Efficient handling of high-load scenarios (bidding, notifications).

3. **Complexity Handling**
   - Thoughtful solutions for nuanced requirements (e.g., escrow payments).

4. **Creativity**
   - Innovative ideas to improve AI recommendations and analytics.

5. **Testing**
   - Comprehensive test coverage with clear documentation.



## Mocking Instructions

### Mock Payments
Use a data structure (e.g., database table or in-memory object) to simulate payments.

#### Example States:
- **pending**: When a client accepts a bid.
- **completed**: After the client approves project delivery.

#### Example Workflow:
- `POST /payments/projects/:id/accept`: Create a payment object in "pending" state.
- `POST /payments/projects/:id/release`: Update the payment object to "completed."

### Mock Notifications
Use a simple queue to simulate real-time notifications.

#### Example Workflow:
- Add notifications to an in-memory queue when relevant events occur (e.g., a new project is posted or a bid is submitted).
- Provide a polling endpoint (e.g., `GET /notifications`) for users to retrieve their notifications.




### ***NOTE**
- There are started code template in the starter-code folder, feel free to use any of these if your work aligns, but this is entirely optional
