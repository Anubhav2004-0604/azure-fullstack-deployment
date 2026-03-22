# Azure Full Stack Deployment

## Overview
This project demonstrates the deployment of a full-stack web application on Microsoft Azure using a secure, scalable, and production-like architecture.

The system is designed with network isolation, secure access, load balancing, and cloud database integration.

---

## Architecture

- VNet1 (Frontend Network)
  - Jump VM (SSH access)
  - 2 Frontend VMs (React + Apache Reverse Proxy)

- VNet2 (Backend Network)
  - 1 Backend VM (Node.js + Express)

- Application Gateway
  - Public entry point for users
  - Handles HTTPS traffic, routing, and load balancing

- Database
  - MongoDB Atlas (cloud-based, secured via IP whitelisting)

---

## Infrastructure Setup

### Virtual Networks
- Created two VNets:
  - VNet1 → Frontend + Jump VM
  - VNet2 → Backend VM
- Configured VNet Peering for secure private communication

---

### Virtual Machines
- Jump VM (Public IP for secure SSH access)
- Frontend VMs (2)
  - Ubuntu + Apache2
  - React application deployed
  - Reverse proxy configured
- Backend VM
  - Ubuntu + Node.js + Express
  - Accessible only via private IP

---

### Application Gateway
- Configured as the public entry point
- Enabled:
  - HTTPS routing
  - Load balancing across frontend VMs
  - Autoscaling
- Integrated with custom domain

---

### Domain Configuration
- Custom domain: amsit.xyz
- Mapped to Application Gateway public IP
- DNS zone configured for routing

---

## Security Implementation

- Backend VM accessible only via private network
- SSH access to internal VMs secured through a Jump VM
- MongoDB Atlas secured using IP whitelisting
- No direct public exposure of backend services

---

## Networking and Routing

- Frontend communicates with backend via private IP
- Reverse proxy (Apache) forwards API requests securely
- VNet Peering enables internal communication between networks

---

## Reverse Proxy Setup

- Enabled Apache modules:
  - proxy
  - proxy_http
  - proxy_headers
- Configured frontend to route API calls to backend private IP

---

## Database Integration

- Used MongoDB Atlas for cloud database
- Created cluster and obtained connection string
- Stored credentials securely using environment variables (.env)
- Backend connects using MongoDB driver

---

## Deployment Process

1. Created Resource Group (Test-rg)
2. Configured VNets and Subnets
3. Deployed Virtual Machines
4. Established VNet Peering
5. Created and configured Application Gateway
6. Deployed frontend and backend applications
7. Configured Reverse Proxy
8. Connected MongoDB Atlas
9. Configured DNS and domain mapping
10. Tested complete application workflow

---

## Documentation

Detailed step-by-step documentation with screenshots and architecture diagrams is available in:

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
