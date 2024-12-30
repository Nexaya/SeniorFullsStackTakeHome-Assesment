# Endpoints and Screens for Assessment

## Endpoints

### 1. User Management

#### **POST /auth/register**
- **Description**: Register a new user (client or freelancer).
- **Payload**:
    ```json
    {
        "username": "string",
        "email": "string",
        "password": "string",
        "role": "client | freelancer"
    }
    ```

#### **POST /auth/login**
- **Description**: Log in a user and generate a JWT.
- **Payload**:
    ```json
    {
        "email": "string",
        "password": "string"
    }
    ```
- **Response**:
    ```json
    {
        "token": "JWT_STRING"
    }
    ```

#### **GET /users/me**
- **Description**: Retrieve user details.
- **Response**:
    ```json
    {
        "id": "int",
        "username": "string",
        "role": "client | freelancer",
        "skills": ["skill1", "skill2"]
    }
    ```

#### **PUT /users/me**
- **Description**: Update user profile (freelancers can add skills and portfolios).
- **Payload (optional)**:
    ```json
    {
        "bio": "string",
        "skills": ["skill1", "skill2"],
        "portfolio": "URL"
    }
    ```

### 2. Project Management

#### **POST /projects**
- **Description**: Create a project (client only).
- **Payload**:
    ```json
    {
        "title": "string",
        "description": "string",
        "budget": "float",
        "skills_required": ["skill1", "skill2"],
        "deadline": "ISO8601_DATE"
    }
    ```
- **Response**: 201 Created

#### **GET /projects**
- **Description**: List all available projects (freelancers can search using query params).
- **Query Parameters**: `?skills=skill1,skill2&budget_min=1000&budget_max=5000`
- **Response**:
    ```json
    [
        {
            "id": "int",
            "title": "string",
            "description": "string",
            "skills_required": ["skill1"],
            "budget": "float",
            "deadline": "ISO8601_DATE"
        }
    ]
    ```

#### **GET /projects/:id**
- **Description**: Retrieve project details.

#### **POST /projects/:id/bids**
- **Description**: Submit a bid on a project (freelancers only).
- **Payload**:
    ```json
    {
        "bid_amount": "float",
        "estimated_delivery_time": "int",
        "proposal": "string"
    }
    ```

#### **GET /projects/:id/bids**
- **Description**: List all bids for a project (clients only).

#### **PUT /projects/:id/bids/:bid_id**
- **Description**: Accept or reject a bid (clients only).
- **Payload**:
    ```json
    {
        "status": "accepted | rejected"
    }
    ```

### 3. AI Recommendation

#### **GET /recommendations/projects**
- **Description**: Retrieve AI-recommended projects for a freelancer.

#### **GET /recommendations/freelancers**
- **Description**: Retrieve AI-recommended freelancers for a project (clients only).

### 4. Payments

#### **POST /payments/projects/:id/accept**
- **Description**: Initiate escrow payment for a project.
- **Payload**:
    ```json
    {
        "payment_method": "string"
    }
    ```

#### **POST /payments/projects/:id/release**
- **Description**: Release payment to freelancer after project approval.

#### **GET /payments/projects/:id/status**
- **Description**: Retrieve payment status.

### 5. Notifications

#### **GET /notifications**
- **Description**: Retrieve real-time notifications.

### 6. Analytics

#### **GET /analytics/freelancer**
- **Description**: Retrieve freelancer analytics.
- **Response**:
    ```json
    {
        "total_earnings": "float",
        "projects_completed": "int",
        "average_rating": "float"
    }
    ```

#### **GET /analytics/client**
- **Description**: Retrieve client analytics.
- **Response**:
    ```json
    {
        "money_spent": "float",
        "average_completion_time": "float",
        "top_freelancers": ["freelancer_id_1", "freelancer_id_2"]
    }
    ```
