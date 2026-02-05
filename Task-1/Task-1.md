# Task: Building a Production-Style Containerized To-Do Application

## Goal:
Build a containerized full-stack web application that exposes a REST API, serves a modern frontend, and uses Docker, Docker Compose, and Nginx following best practices for service isolation, networking, and configuration.

The task focuses on understanding how frontend, backend, and infrastructure components interact in real-world systems rather than just building a working UI.

## Deliverables:
A full-stack To-Do application consisting of:

- A REST API backend for managing tasks
- A frontend web application for interacting with the API
- A containerized environment using Docker and Docker Compose
- A reverse proxy that exposes the application cleanly to users

All components must run inside containers and communicate over Docker-managed networks.

## 1. Backend: To-Do API Service
**Objective**:
- Implement a backend service that manages to-do items and exposes a RESTful API using Django + Django REST Framework, backed by a PostgreSQL database for persistent storage.

**Requirements**:
- Design a relational data model for a to-do item stored in PostgreSQL
- The model should support basic task attributes (content, status, timestamps, etc.)
- Database migrations must be part of the setup workflow
- Expose REST endpoints to:
  - Create a to-do
  - Fetch all to-dos
  - Update a to-do
  - Delete a to-do
- Use environment variables for configuration
- Ensure the API is designed to be consumed by an external frontend
- Include a basic health check endpoint to verify service availability and database connectivity

**Expected Output:**
- A fully functional Django REST API backed by PostgreSQL
- Database schema created and managed via migrations
- Clear documentation of API endpoints

## 2. Frontend: To-Do Web Application
**Objective**: 

Build a frontend application that consumes the backend API and provides an interactive UI for users using Vite with optional Tailwind CSS integration.

**Requirements:**
- Display a list of to-do items retrieved from the backend
- Allow users to perform CRUD operations on to-do list items.
- Backend API URL should be configurable via environment variables
- UI/UX decisions are flexible

**Expected Output:**
- A frontend that communicates only via the API
- No backend logic embedded in frontend code

## 3. Containerization of Services
**Objective:**

Package frontend and backend as independent Docker services.

**Requirements:**

- Create separate Dockerfiles for:
  - Backend service
  - Frontend service
- PostgreSQL should run as a dedicated container
- Each container should:
  - Be reproducible
  - Run independently
  - Use environment variables for configuration
  - Avoid hardcoded secrets or URLs

**Expected Output:**
- Two Docker images that can be built and run independently
- Clean, readable Dockerfiles

## 4. Service Orchestration with Docker Compose
**Objective:**

Run the entire application stack using a single orchestration configuration using Docker Compose.

**Requirements:**

- Define services for:
  - Backend (Django + DRF)
  - Frontend (Vite)
  - Database (PostgreSQL)
  - Reverse proxy (Nginx)
- Use:
  - Custom Docker networks for service communication
  - Named volumes for PostgreSQL data persistence
- Ensure internal services communicate via Docker networking
- Expose only necessary ports to the host system

**Expected Output:**
- A docker-compose.yml file that brings up the full system with one command

## 5. Reverse Proxy & Routing
**Objective:**
Expose the application through a single entry point using a reverse proxy (Nginx).

**Requirements:**

- Configure routing such that:
  - API requests are forwarded to the backend service
  - Frontend traffic is served correctly
  - Backend and PostgreSQL services should not be directly exposed to users

**Expected Output:**
- Application accessible through a single URL
- Clear separation between internal services and public access
