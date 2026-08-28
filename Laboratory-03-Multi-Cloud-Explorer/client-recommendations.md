## Client A – Startup Company

**Recommended Platform:** AWS

**Justification:** AWS offers a generous free tier and flexible pay-as-you-go pricing, which fits a startup with a limited budget. It also scales easily as the app grows, so the company won't need to migrate to a different provider later as demand increases. AWS's large ecosystem of tools and extensive documentation make it easier for a small team to build and launch quickly without needing a large IT staff.

**Relevant Services:**

- Amazon EC2 (hosting the mobile app backend)
- Amazon S3 (storing app files, images, and user data)
- AWS Lambda (serverless functions to keep costs low while scaling)

---

## Client B – University

**Recommended Platform:** Microsoft Azure

**Justification:** Since the university already runs Windows Server, Microsoft 365, and Active Directory, Azure offers the smoothest migration path with minimal disruption to existing systems. It integrates directly with their current identity setup, so users and permissions carry over without needing to be rebuilt. This also reduces the learning curve for IT staff already familiar with Microsoft tools, saving time and training costs.

**Relevant Services:**

- Azure Virtual Machines (migrating on-premises servers to the cloud)
- Microsoft Entra ID (identity management tied to their existing Active Directory)
- Azure SQL Database (hosting university databases)

---

## Client D – Global E-Commerce Company

**Recommended Platform:** AWS

**Justification:** AWS has the widest global infrastructure of any provider, with the most regions and edge locations, allowing fast, reliable access for customers around the world. Its auto-scaling features handle sudden traffic spikes, such as sales events or holiday shopping, without downtime. AWS also has a long track record of supporting large-scale, mission-critical applications, making it a safe choice for a business that can't afford outages.

**Relevant Services:**

- Amazon EC2 with Auto Scaling (handling traffic spikes automatically)
- Amazon CloudFront (fast global content delivery via CDN)
- Amazon RDS (reliable, managed database for order/customer data)

## Decision Matrix

| Business Requirement | Recommended Platform | Justification |
|---|---|---|
| Startup Company | AWS | Low-cost entry with flexible scaling |
| Enterprise Organization | AWS | Broadest range of services and proven reliability |
| Microsoft Environment | Azure | Best integration with Microsoft tools |
| AI / Machine Learning | GCP | Strongest AI/ML tools and infrastructure |
| Kubernetes Deployment | GCP | GKE, since Google created Kubernetes |
| Global Web Application | AWS | Widest global infrastructure with auto-scaling |
