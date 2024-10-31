# Intra 75

Welcome to [**Intra 75**]()! The goal of this project is to create a fun way for students to learn by doing.

Students will complete projects on the intranet and gain experience to level up your skills! Your skill level on the Intra is a fun way to estimate your overall experience and how much you can do!

Be sure to give it your all!

## Registration

All students on the intra must be registered and logged in before they can access the intranet's resources!

Please register at your earliest convenience.

# Project Schema

![A visual representation of the database schema](/docs/prisma-erd.svg)

1. Create a new Postgres database named `intra`.
2. Initialize Prisma and connect it to the database.
3. Define the models according to the schema above.
4. The database will be seeded with 25 projects.

## API

Using Express, we will accomplish the following.

The 🔒 lock icon next to a route indicates that it must be protected via authentication. A user can only access this route by attaching a valid token to the request. If a token is not provided, a 401 Unauthorized error is returned.

### Authentication

- `POST /register` creates a new Student with the provided credentials and returns a token
  - the `request` body should include a `username` and `password`
  - the `request` body can optionally include other user info, such as `name` and `email`
  - the `password` should be hashed in the database
- `POST /login` attempts to validate the provided credentials and returns a token if successful
  - the `request` body should include a username and password

### User Profile

- `GET /profile/:username` returns any public information related to the given username
  - return the user's `full name`, `experience`, and `level`
  - if the user does not exist, return 404 Not Found
- 🔒 `GET /info` returns all information related to the logged in user
  - returns a `JSON` object containing the user's username, email, experience, and current level

### Projects

- 🔒 `GET /projects` returns a list of all projects
- 🔒 `GET /projects/:id` returns a specific project

### Assignments

- 🔒 `GET /log` returns a list of all projects currently assigned to the Studen
