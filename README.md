
# Flask Authentication System with PostgreSQL and Docker

This project is a simple Flask web application that implements a user authentication system. It allows users to register and log in using a username and password. The passwords are securely hashed and stored in a PostgreSQL database. The project is Dockerized, so you can easily deploy it as a containerized application.

## Features

- User registration with username and password.
- Password hashing using Flask-Bcrypt for secure storage.
- PostgreSQL as the database for storing user credentials.
- Dockerized application with Flask and PostgreSQL running in separate containers.
- Docker Compose to easily manage and run the application.

## Technologies Used

- **Flask**: The web framework used to build the application.
- **Flask-SQLAlchemy**: Extension for Flask to simplify integration with SQLAlchemy, the ORM for PostgreSQL.
- **PostgreSQL**: Database used to store user credentials.
- **Flask-Bcrypt**: Library to hash passwords securely.
- **Docker**: Containerization of the Flask application and PostgreSQL database.
- **Docker Compose**: Tool to define and run multi-container Docker applications.

## Prerequisites

Before you begin, ensure you have the following software installed:

- [Docker](https://www.docker.com/products/docker-desktop)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [Python 3.x](https://www.python.org/)

## Installation

1. Clone this repository to your local machine:
   ```bash
   git clone https://github.com/yourusername/flask-auth-postgres-docker.git
   cd flask-auth-postgres-docker
   ```

2. Build and run the Docker containers using Docker Compose:
   ```bash
   docker-compose up --build
   ```

   This command will:
   - Build the Flask app container.
   - Pull the PostgreSQL image and create a database container.
   - Start both containers and link them together.

3. Access the application:
   Open your browser and go to `http://localhost:5000`. You should see the Flask application running.

## Environment Variables

The project requires an environment variable `DATABASE_URL` to connect to the PostgreSQL database. It should be set in a `.env` file in the project root directory.

Here’s an example of the `.env` file:

```env
DATABASE_URL=postgresql://flaskuser:flaskpass@db:5432/flaskdb
```

- **flaskuser**: The PostgreSQL username.
- **flaskpass**: The PostgreSQL password.
- **db**: The name of the PostgreSQL service (matches the Docker Compose service name).
- **flaskdb**: The name of the PostgreSQL database.

## Usage

### User Registration

1. Go to the registration page (e.g., `http://localhost:5000/register`).
2. Enter a username and password.
3. The password will be securely hashed using **Flask-Bcrypt** and stored in the PostgreSQL database.

### User Login

1. Go to the login page (e.g., `http://localhost:5000/login`).
2. Enter your username and password.
3. The entered password will be compared with the hashed password in the database. If it matches, the login will be successful.

## Directory Structure

```
flask-auth-postgres-docker/
│
├── app/
│   ├── app.py             # Main Flask application file
│   ├── models.py          # Database models (User model)
│   └── requirements.txt   # Python dependencies
│
├── .env                   # Environment variables (including DATABASE_URL)
├── Dockerfile             # Dockerfile for the Flask application
├── docker-compose.yml     # Docker Compose configuration
└── README.md              # This readme file
```

## Docker Configuration

### Dockerfile

The `Dockerfile` defines the image for the Flask app. It uses the official Python image, installs dependencies, and runs the app.


### docker-compose.yml

The `docker-compose.yml` file defines two services: `flask_app` (for the Flask application) and `db` (for the PostgreSQL database).



- **`flask_app`**: Builds the Flask app container and exposes port 5000 for access to the app.
- **`db`**: Runs a PostgreSQL container, with environment variables for setting up the database and user credentials.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

This `README.md` file explains how to set up, configure, and run the Flask authentication system with PostgreSQL and Docker. It provides clear instructions for users and developers who want to deploy the application locally or in a containerized environment.