# Expense Splitter
Full-stack web application for managing shared expenses in groups.

Users can create groups, add members, record expenses and automatically calculate balances and settlement suggestions between participants.

This project is structured as a **monorepo** containing both the backend API and the frontend application.

The frontend is intentionally lightweight and serves mainly as a client for interacting with and testing the backend API.

## Table of contents
- [Screenshots](#screenshots)
- [Tech stack](#tech-stack)
- [Main features](#main-features)
- [Running locally](#running-locally)
- [What I practiced in this project](#what-i-practiced-in-this-project)

## Screenshots

### Registration page
<img src="https://i.imgur.com/bszz6bQ.png">

Account creation page that allows new users to register in the system.

During registration the user provides basic credentials such as email and password.  
The password is securely hashed on the backend before being stored in the database.

### Login page
<img src="https://i.imgur.com/wcXVnVX.png">

User authentication page allowing existing users to sign in to the application.

Users provide their email and password to receive a **JWT authentication token**, which is then used to authorize further API requests.

### Dashboard
<img src="https://i.imgur.com/Vi8pH5t.png">

The main view of the application showing existing expense groups.  
Users can quickly access a group, view balances or create a new expense group.

### Group info
<img src="https://i.imgur.com/L932Ceu.png">

View of a selected group.  
Displays the name, owner, date of creation, and number of members.

### Balances and settlement suggestions

<img src="https://i.imgur.com/25eflUp.png">

Automatically calculated balances between group members.  
The application shows who owes money to whom and suggests the simplest settlements.

### Adding a new expense
<img src="https://i.imgur.com/YYlamKa.png">

Form used to add a new expense to the group.  
The user can define the title, amount, payer and select participants involved in the expense.

### Expenses list

<img src="https://i.imgur.com/WB53oDz.png">

List of all expenses recorded in the group.  
Each expense shows who paid, the amount and allows easy tracking of shared costs.

### Group members management

<img src="https://i.imgur.com/gH69WOw.png">

View for managing group members.  
Users can see all participants and add new members to the expense group.

## Tech Stack
### Backend
- <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/dotnetcore/dotnetcore-original.svg" height="20"/> ASP.NET Core Web API  
- <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg" height="20"/> C#  
- <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/postgresql/postgresql-original.svg" height="20"/> PostgreSQL  
- <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/dotnetcore/dotnetcore-original.svg" height="20"/> Entity Framework Core
- <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg" height="20"/> Docker  
- <img src="https://cdn.simpleicons.org/jsonwebtokens/white" height="20"/> JSON Web Token (JWT)
### Frontend
- <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" height="20"/> React  
- <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" height="20"/> TypeScript  
- <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" height="20"/> HTML5  
- <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" height="20"/> CSS3  
- <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vitejs/vitejs-original.svg" height="20"/> Vite
- <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/axios/axios-plain.svg" height="20"/> Axios  
- <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/reactrouter/reactrouter-original.svg" height="20"/> React Router

## Main features
-   Create and manage expense groups    
-   Add members to groups by email    
-   Record shared expenses    
-   Automatically calculate balances for each member    
-   Generate settlement suggestions to minimize transfers    
-   JWT authentication and protected routes    
-   Clean UI with responsive layout

## Architecture

The project follows a layered backend architecture:

- **API layer** – ASP.NET Core controllers handling HTTP requests
- **Application layer** – business logic and services
- **Infrastructure layer** – database access using Entity Framework Core
- **Database layer** – PostgreSQL

The frontend communicates with the backend through REST API endpoints.

## Running locally
### Prerequisites
Make sure you have the following tools installed:
-   .NET SDK  
-   EF Core CLI   
-   Docker   
-   Git

**Clone the repository**
```
git clone https://github.com/marybrown123/expense-splitter.git
```
```
cd expense-splitter
```

### Backend
1. **Go to backend directory**
```
cd backend
```
2. **Start database**
The project uses PostgreSQL running in Docker.
```
docker compose up -d
```
3. **Apply database migrations**
```
dotnet ef database update --project ExpenseSplitter.Infrastructure --startup-project ExpenseSplitter.Api
```
4. **Run the API**
```
dotnet run --project ExpenseSplitter.Api
```
The API will start on:
http://localhost:5000

5. **Open Swagger**
After starting the application, open:
http://localhost:5000/swagger

### Frontend
1. **Go to frontend directory**
```
cd ..
```
```
cd frontend
```
2. **Install dependencies**
```
npm install
```
3. **Add `.env` file**
```
VITE_API_URL=http://localhost:5000/api
```
4. **Start the application**
```
npm run dev
```
Frontend will run on:
http://localhost:5173

## What I practiced in this project
- designing and implementing a full-stack web application  
- building a REST API using ASP.NET Core  
- structuring a layered backend architecture (Clean Architecture principles)  
- working with PostgreSQL and Entity Framework Core  
- implementing JWT authentication and protected API endpoints  
- handling relational data models and database migrations  
- developing a React frontend using TypeScript  
- client-side routing with React Router  
- communicating with backend services using Axios  
- building reusable UI components  
- implementing expense splitting and balance calculation algorithms  
- generating settlement suggestions to minimize transfers between users


## Project history

Originally the frontend and backend were developed as separate repositories:

- Backend: https://github.com/marybrown123/expense-splitter-backend
- Frontend: https://github.com/marybrown123/expense-splitter-frontend

Later they were merged into a monorepo to simplify development and deployment.