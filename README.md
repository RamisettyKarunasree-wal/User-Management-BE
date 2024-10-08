<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo-small.svg" width="200" alt="Nest Logo" /></a>
</p>

[circleci-image]: https://img.shields.io/circleci/build/github/nestjs/nest/master?token=abc123def456
[circleci-url]: https://circleci.com/gh/nestjs/nest

<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=nodejs,ts,nestjs,mongodb,npm" />
  </a>
</p>
<p align="center">A comprehensive <a href="https://github.com/nestjs/nest" target="_blank">Nest.js</a> application for managing user authentication and authorization with OAuth support for Google and LinkedIn.</p>

## Description

This repository contains a **User Management System** built with **NestJS** and **MongoDB**, supporting features like user registration, login, profile management, and authentication using **OAuth** strategies for Google and LinkedIn. It also leverages [Nest](https://github.com/nestjs/nest) framework's TypeScript starter repository, combined with **Passport.js** for secure OAuth login integration.

## Features

- **User Registration** and **Login** with JWT authentication
- **OAuth Login** using Google and LinkedIn
- **Profile Management** for authenticated users
- **Nodemailer** integration for sending registration success emails
- Built-in test framework support (unit tests, e2e tests, and test coverage)

## Prerequisites for OAuth

Before using Google and LinkedIn OAuth, you'll need to:

1. **Create a Google OAuth app**:

   - Visit [Google Developers Console](https://console.cloud.google.com/).
   - Create a new project.
   - Under "APIs & Services," navigate to "Credentials" and set up an OAuth 2.0 Client ID.
   - Set the **authorized redirect URIs** for your app (e.g., `http://localhost:3000/auth/google/callback`).
   - Get your **Client ID** and **Client Secret**.

2. **Create a LinkedIn OAuth app**:
   - Visit [LinkedIn Developer Portal](https://www.linkedin.com/developers/).
   - Create a new application.
   - Configure the **OAuth 2.0 Redirect URL** (e.g., `http://localhost:3000/auth/linkedin/callback`).
   - Get your **Client ID** and **Client Secret**.

## Installation

1. Clone or download this repository:

```bash
$ git clone <repository-url>
$ cd user-management-nestjs

```

## OAuth Routes

Google OAuth Login: /auth/google

Google OAuth Callback: /auth/google/callback

LinkedIn OAuth Login: /auth/linkedin

LinkedIn OAuth Callback: /auth/linkedin/callback

## Project Structure

src/
|-- auth/ # OAuth strategies for Google and LinkedIn, and JWT authentication
|-- user/ # User management including registration, login, and profile
|-- mail/ # Nodemailer integration for sending success emails
|-- app.module.ts # Main application file
|-- main.ts # Entry point of the application
|-- tests/ # Unit and integration tests

### Key Updates:

1. Added OAuth integration details for Google and LinkedIn using Passport.js.
2. Described how to create OAuth apps in Google Developers Console and LinkedIn Developer Portal.
3. Explained `.env` configuration and necessary variables.
4. Highlighted OAuth login routes and app structure for clarity.

Let me know if any further adjustments are needed!
