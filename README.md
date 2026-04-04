# aws-grocery-aggregator-service


nfrastructure & Deployment

This project is deployed on an **AWS EC2** instance running Ubuntu 22.04.

Cloud Configuration
* **Environment:** AWS t2.micro (Free Tier)
* **Backend:** Spring Boot (Java 17)
* **Deployment:** Managed via SSH; utilized `nohup` for background process persistence.
* **Networking:** Configured Inbound Security Group rules for Port 8080.

 API Validation
Verified all REST endpoints using **Postman** to ensure 200 OK status and correct JSON schema delivery.

| Endpoint | Method | Purpose |
| :--- | :--- | :--- |
| `/products/search` | `GET` | Filtered grocery data by name |
| `/products/best-deal` | `GET` | Price aggregation and comparison |

---
