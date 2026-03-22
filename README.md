# Azure Full Stack Deployment

## Overview
This project demonstrates the deployment of a full-stack web application on Microsoft Azure using a secure, scalable, and production-like architecture.

The system is designed with proper network isolation, secure access, load balancing, and cloud database integration.

---

## Architecture

- VNet1 (Frontend Network)
  - Jump VM (SSH access)
  - 2 Frontend VMs (React + Apache Reverse Proxy)

- VNet2 (Backend Network)
  - 1 Backend VM (Node.js + Express)

- Application Gateway
  - Acts as public entry point
  - Handles HTTPS, routing, and load balancing

- Database
  - MongoDB Atlas (cloud-based, secured via IP whitelisting)

---

## Infrastructure Setup

### Virtual Networks
- Created two VNets:
  - VNet1 → Frontend + Jump VM
  - VNet2 → Backend VM
- Configured VNet Peering for private communication

---

### Virtual Machines
- Jump VM (Public IP for SSH access)
- Frontend VMs (2)
  - Ubuntu + Apache2
  - React application deployed
  - Reverse proxy configured
- Backend VM
  - Ubuntu + Node.js + Express
  - Runs on private IP only

---

### Application Gateway
- Configured as public entry point
- Enabled:
  - HTTPS routing
  - Load balancing across frontend VMs
  - Autoscaling
- Connected with custom domain

---

### Domain Configuration
- Custom domain: amsit.xyz
- Mapped to Application Gateway public IP
- DNS zone configured for routing

---

## Security Implementation

- Backend VM accessible only via private network
- SSH access restricted via Jump VM
- MongoDB Atlas secured using IP whitelisting
- No direct public exposure of backend services

---

## Networking & Routing

- Frontend communicates with backend via private IP
- Reverse proxy (Apache) forwards API requests
- VNet Peering enables secure internal communication

---

## Reverse Proxy Setup

- Enabled Apache modules:
  - proxy
  - proxy_http
  - proxy_headers
- Configured frontend to route API calls to backend private IP

---

## Database Integration

- Used MongoDB Atlas
- Created cluster and obtained connection string
- Stored in .env file securely
- Backend connects using MongoDB driver

---

## Deployment Process

1. Created Resource Group (Test-rg)
2. Setup VNets and Subnets
3. Deployed Virtual Machines
4. Configured VNet Peering
5. Created Application Gateway
6. Deployed frontend and backend code
7. Configured Reverse Proxy
8. Connected MongoDB Atlas
9. Configured DNS and domain mapping
10. Tested full application flow

---

## Documentation

Detailed step-by-step documentation with screenshots and diagrams is available here:

Full-Stack App Deployment-project.docx

---

## Key Learnings

- Azure cloud infrastructure setup
- Virtual Network design and peering
- Secure system architecture using Jump VM
- Load balancing using Application Gateway
- Reverse proxy configuration
- Full-stack deployment (Frontend and Backend)
- Cloud database integration (MongoDB Atlas)

---

## Conclusion

This project demonstrates a production-like cloud architecture with:
- Secure communication
- Scalable frontend
- Isolated backend
- Domain-based access
- End-to-end deployment on Azure

For detailed documentation, please download the project file:
Full-Stack App Deployment-project.docx
