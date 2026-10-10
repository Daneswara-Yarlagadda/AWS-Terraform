from pathlib import Path

content = r"""# Cloud Fundamentals Notes

## ISP vs CSP vs Infrastructure vs Scaling vs Load Balancer vs DNS Flow

---

## 1. ISP (Internet Service Provider)

### What is ISP?

An **ISP** is a company that provides **internet connectivity** to homes, offices, data centers, and cloud networks.

### What ISP actually gives you

- Internet connection (fiber/broadband/leased line)
- Public IP (static or dynamic)
- Bandwidth plan (100 Mbps, 1 Gbps, etc.)
- Routing to the internet (BGP behind the scenes)
- Sometimes: basic firewall / DDoS protection (depends on provider)

### Examples (for understanding)

- Airtel, Jio, BSNL, ACT, Hathaway
- Enterprise: Tata Communications, Vodafone Business, etc.

### Why ISP matters in Infra/Cloud

Without ISP:

- Your office cannot access AWS console
- Your users cannot reach your website
- Your data center cannot connect to the world

---

## 2. CSP (Cloud Service Provider)

### What is CSP?

A **CSP** is a company that provides **IT infrastructure as a service** (servers, storage, networks, databases, security) over the internet.

### What CSP provides

- Compute (servers / VMs)
- Storage (object/block/file)
- Networking (VPC, subnets, routing, firewall controls)
- Security services (IAM, encryption, monitoring)
- Managed services (DB, Kubernetes, queues, CDN)

### Examples

- AWS, Azure, GCP

### Key difference (ISP vs CSP)

- **ISP gives internet**
- **CSP gives IT infrastructure over internet**

Think like this:

- ISP = Road
- CSP = City (buildings, power, services inside the city)

---

## 3. What is “Infrastructure” (Infra)

### Meaning

**Infrastructure** is the complete setup needed to run an application reliably:

- Servers
- Network
- Security
- Storage
- Databases
- Monitoring
- Scaling and failover

### Infra in simple line

Infra is **everything behind the application** that makes it reachable, fast, and safe.

---

## 4. Core Infra Components

### webserver + app + db + storage + network + firewall

Let’s break it down clearly.

### A) Web Server

**Role:** Handles incoming HTTP/HTTPS requests from users.

Common web servers:

- Nginx
- Apache
- IIS

Responsibilities:

- Terminate SSL (sometimes)
- Serve static files
- Reverse proxy to application
- Basic caching and compression

### B) Application Server (App)

**Role:** Runs your business logic.

Examples:

- Java (Tomcat/Spring Boot)
- Node.js
- Python (Flask/Django)
- .NET

Responsibilities:

- Login, validation, rules, workflows
- Talks to DB and other services
- Generates API response / HTML response

### C) Database (DB)

**Role:** Stores structured data permanently.

Examples:

- MySQL, PostgreSQL, Oracle, SQL Server
- NoSQL: DynamoDB, MongoDB

Responsibilities:

- Transactions
- Data integrity
- Querying, indexing
- Backup and restore

### D) Storage

**Role:** Stores files and objects (images, PDFs, logs, backups, videos).

Types:

- Block Storage (like disk attached to server)
- Object Storage (S3 type)
- File Storage (shared filesystem)

Use cases:

- User uploads
- Reports
- Application logs
- Backups

### E) Network

**Role:** Connects everything together securely.

Includes:

- VPC / network boundary
- Subnets (public/private)
- Route tables
- Internet Gateway / NAT
- DNS and IP addressing

### F) Firewall (Security Layer)

**Role:** Controls traffic. Allows only required ports from allowed sources.

In cloud, firewall is mainly:

- Security Groups (instance-level)
- Network ACLs (subnet-level)
- WAF (web firewall for HTTP attacks)

Example rules:

- Allow 443 from internet to Load Balancer
- Allow 8080 from Load Balancer to App servers
- Allow 3306 only from App to DB

---

## 5. Scaling (Most Important Production Concept)

### What is Scaling?

Scaling means increasing capacity when traffic increases, and reducing when traffic decreases.

Two main types:

### A) Vertical Scaling (Scale Up)

Increase server size:

- 2 vCPU → 8 vCPU
- 4 GB RAM → 32 GB RAM

**Pros:**

- Simple

**Cons:**

- Has a limit
- Might require downtime
- Not
