# Project Name

## Description
This project consists of a frontend and backend. The backend is built using Node.js and the frontend uses your preferred framework (e.g., React). This document explains how to set up, run, and deploy both the frontend and backend using Docker.

## Prerequisites

Before you begin, make sure you have the following installed:
- Docker: [Installation Guide](https://docs.docker.com/get-docker/)
- Node.js (for local development): [Installation Guide](https://nodejs.org/)
- Docker Compose: [Installation Guide](https://docs.docker.com/compose/install/)

## Project Setup

### 1. Backend Setup

#### Local Development

1. Go to the backend folder:
    ```bash
    cd backend
    ```

2. Install dependencies:
    ```bash
    npm install
    ```

3. Start the backend server:
    ```bash
    node src/app.js
    ```

    The server will be running at `http://localhost:5001`.

#### Docker Setup

To run the backend using Docker, follow these steps:

1. Build the Docker image:
    ```bash
    docker build -t backend .
    ```

2. Run the backend container:
    ```bash
    docker run -d -p 5001:5001 backend
    ```

    The backend will be accessible at `http://localhost:5001`.

### 2. Frontend Setup

#### Local Development

1. Go to the frontend folder:
    ```bash
    cd frontend
    ```

2. Install dependencies:
    ```bash
    npm install
    ```

3. Start the development server:
    ```bash
    npm run dev
    ```

    The frontend will be available at `http://localhost:5174`.

#### Docker Setup

To run the frontend using Docker, follow these steps:

1. Build the Docker image:
    ```bash
    docker build -t frontend .
    ```

2. Run the frontend container:
    ```bash
    docker run -d -p 80:80 frontend
    ```

    The frontend will be accessible at `http://localhost`.

### 3. Running with Docker Compose

To simplify running both the frontend and backend together, you can use Docker Compose.

1. Ensure you have a `docker-compose.yml` file at the root of your project. It should look like this:

    ```yaml
    version: '3'
    services:
      backend:
        build:
          context: ./backend
          dockerfile: Dockerfile
        ports:
          - "5001:5001"

      frontend:
        build:
          context: ./frontend
          dockerfile: Dockerfile
        ports:
          - "80:80"
    ```

2. Build and run both services:
    ```bash
    docker-compose up --build
    ```

    This command will build both the frontend and backend images and run them. The frontend will be accessible at `http://localhost` and the backend will be available at `http://localhost:5001`.

### 4. Testing the Application

To verify that both services are working properly:

- Visit `http://localhost` to check the frontend.
- Visit `http://localhost:5001` to check if the backend is running.
- Ensure there are no errors in the console logs.


