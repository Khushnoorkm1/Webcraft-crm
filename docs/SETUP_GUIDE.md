# Webcraft CRM - Complete Setup Guide

## Table of Contents
- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)

## Overview

Webcraft CRM is a comprehensive customer relationship management system designed to streamline business operations and enhance customer interactions.

## Prerequisites

Before setting up Webcraft CRM, ensure you have the following installed:

- **Node.js** (v14.0.0 or higher)
- **npm** (v6.0.0 or higher) or **yarn** (v1.22.0 or higher)
- **Git** (v2.0.0 or higher)
- **Database**: PostgreSQL (v12.0 or higher) or MongoDB (v4.4 or higher)
- **Git** for version control

## Installation

### Step 1: Clone the Repository

```bash
git clone https://github.com/Khushnoorkm1/Webcraft-crm.git
cd Webcraft-crm
```

### Step 2: Install Dependencies

Using npm:
```bash
npm install
```

Or using yarn:
```bash
yarn install
```

### Step 3: Set Up Environment Variables

Create a `.env` file in the root directory:

```bash
cp .env.example .env
```

Edit the `.env` file and configure the following variables:

```
NODE_ENV=development
PORT=3000
DATABASE_URL=postgresql://user:password@localhost:5432/webcraft_crm
JWT_SECRET=your_jwt_secret_key_here
API_KEY=your_api_key_here
```

### Step 4: Initialize the Database

```bash
npm run db:migrate
npm run db:seed
```

## Configuration

### Database Configuration

Update your database connection string in the `.env` file:

- **PostgreSQL**: `postgresql://username:password@localhost:5432/dbname`
- **MongoDB**: `mongodb://username:password@localhost:27017/dbname`

### Authentication Setup

1. Generate a secure JWT secret:
   ```bash
   node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"
   ```

2. Add the generated secret to your `.env` file as `JWT_SECRET`

### Email Configuration (Optional)

To enable email notifications, configure SMTP settings in `.env`:

```
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your_email@gmail.com
SMTP_PASSWORD=your_app_password
```

## Running the Application

### Development Mode

```bash
npm run dev
```

The application will start on `http://localhost:3000`

### Production Mode

```bash
npm run build
npm start
```

### Running Tests

```bash
npm test
```

For coverage report:
```bash
npm run test:coverage
```

## Troubleshooting

### Common Issues

#### 1. Database Connection Error

**Problem**: `Error: connect ECONNREFUSED 127.0.0.1:5432`

**Solution**:
- Ensure PostgreSQL/MongoDB is running
- Verify database credentials in `.env`
- Check if the database exists

#### 2. Port Already in Use

**Problem**: `Error: listen EADDRINUSE: address already in use :::3000`

**Solution**:
- Change the PORT in `.env` file
- Or kill the process using port 3000:
  ```bash
  lsof -ti:3000 | xargs kill -9
  ```

#### 3. Dependencies Installation Failed

**Problem**: `npm ERR! code ERESOLVE`

**Solution**:
```bash
npm install --legacy-peer-deps
```

#### 4. Environment Variables Not Loading

**Problem**: Variables from `.env` are undefined

**Solution**:
- Ensure `.env` file is in the root directory
- Restart the development server
- Check for typos in variable names

## Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m 'Add your feature'`
4. Push to the branch: `git push origin feature/your-feature`
5. Submit a pull request

### Code Standards

- Follow ESLint configuration
- Write meaningful commit messages
- Add tests for new features
- Update documentation as needed

## Support

For issues and questions:
- Open an issue on GitHub
- Contact: khushnoor19921992@gmail.com

## License

This project is licensed under the MIT License - see the LICENSE file for details.

---

**Last Updated**: May 3, 2026
