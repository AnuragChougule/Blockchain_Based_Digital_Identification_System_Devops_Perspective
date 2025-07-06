# DevOps Blockchain Project

Welcome to the **DevOps** repository! This project leverages blockchain technology, primarily using **Solidity** for smart contracts and a full-stack application built with **JavaScript**, **HTML**, and **CSS**. The project demonstrates a complete CI/CD pipeline with integration to Ethereum development tools such as **Truffle** and **Ganache**, and deploys the front end using **Nginx**.
### CI/CD Workflow
![CI/CD Workflow](https://github.com/user-attachments/assets/bb0b2a26-c181-4a5e-9f8f-d1a01fc51ad5)

### Smart Contracts
![Smart Contract Overview](https://github.com/user-attachments/assets/71c0f398-a7f0-4bc9-8c07-c41f720c5d1a)


---

## Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation & Execution Steps](#installation--execution-steps)
- [CI/CD Pipeline (`.github/workflows/ci-cd.yml`)](#cicd-pipeline)
- [Project Structure](#project-structure)
- [Images](#images)
- [License](#license)

---

## Features

- Blockchain-based application with smart contracts in Solidity.
- Node.js backend and HTML/CSS/JavaScript frontend.
- Automated testing and deployment with GitHub Actions.
- Local blockchain development with Ganache & Truffle.
- Frontend deployment to Nginx web server.

---

## Prerequisites

- Ubuntu/Debian-based system
- Node.js & npm
- Git
- Ganache CLI
- Truffle Suite
- Nginx

---

## Installation & Execution Steps

Follow these steps to set up and run the project:

```bash
# 1. Update packages and install dependencies
sudo apt update
sudo apt install nodejs npm git

# 2. Verify installations
node -v && npm -v

# 3. Clone the repository
git clone https://github.com/AnuragChougule/DevOps.git
cd DevOps

# 4. Set up backend
cd backend
rm -rf node_modules
rm package-lock.json
npm install
npm start
npm install
node app.js

# 5. Set up Blockchain environment
cd ..
sudo npm install -g ganache-cli
sudo ganache-cli -p 7545 

# 6. Compile & migrate smart contracts
cd truffle
truffle compile
truffle migrate --network development
cd ..

# 7. Deploy frontend to Nginx
sudo apt install nginx
sudo systemctl restart nginx
sudo cp -r ~/DevOps/frontend/* /var/www/html/
sudo systemctl restart nginx
```

---

## CI/CD Pipeline

This project uses GitHub Actions for Continuous Integration and Continuous Deployment. Below is the workflow YAML file located at `.github/workflows/ci-cd.yml`:

```yaml
name: CI/CD Pipeline

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build-and-test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Set up Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'

      - name: Install backend dependencies
        run: |
          cd backend
          npm install

      - name: Run backend tests
        run: |
          cd backend
          npm test

      - name: Install truffle and ganache-cli
        run: |
          npm install -g truffle ganache-cli

      - name: Compile smart contracts
        run: |
          cd truffle
          truffle compile

      - name: Lint frontend code
        run: |
          cd frontend
          npm install
          npm run lint

      - name: Deploy to server (example step)
        if: github.ref == 'refs/heads/main'
        run: echo "Deploy step goes here"
```

---

## Project Structure

```
DevOps/
├── backend/
│   └── ... (Node.js code)
├── frontend/
│   └── ... (HTML/CSS/JS)
├── truffle/
│   └── ... (Solidity contracts, migrations)
├── .github/
│   └── workflows/
│       └── ci-cd.yml
└── README.md
```

---

## Images

- Place your images in the `images/` directory for easy reference in documentation.
- Example images include architecture diagrams, workflow charts, and UI screenshots.

---

## License

This project is licensed under the [MIT License](LICENSE).

---

> 📧 For queries, reach out at: [anuragchougule0160@gmail.com]
