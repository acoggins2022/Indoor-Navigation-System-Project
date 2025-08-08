# Indoor Navigation System for Mobility Impaired Individuals

This repository serves as a detailed project summary and architectural overview for my senior engineering design project at Florida Atlantic University, "Turn Unknown Spaces into Familiar Places." The source code is proprietary to the university and cannot be shared publicly.

---

## Project Overview

This project was a full-stack indoor navigation system developed by a team to assist individuals with mobility impairments in navigating complex indoor environments. The system provided users with accessible routes, avoiding obstacles like stairs and highlighting features such as ramps and elevators.

As the **Backend and Cloud Lead**, I was solely responsible for designing, implementing, and securing the entire cloud-based backend infrastructure on Amazon Web Services (AWS).

---

## My Role & Responsibilities

My primary responsibilities were focused on creating a secure, scalable, and cost-effective backend to support the client-side application.

* **Cloud Architecture:** Designed a serverless architecture on AWS to handle API requests, data storage, and business logic.
* **Database Design:** Engineered the relational database schema in PostgreSQL to efficiently store and query building layouts, points of interest (POIs), user data, and accessible pathways.
* **API Development:** Developed a comprehensive REST API using Python and the Flask framework to serve as the communication layer between the frontend application and the backend database.
* **Security Implementation:** Integrated security best practices throughout the development lifecycle, focusing on network isolation, access control, and data protection.

---

## Technical Architecture & Security Considerations

The backend was designed with a security-first approach, ensuring that the infrastructure was protected from common threats and that data was handled responsibly.

### Secure Cloud Architecture

The infrastructure was built within a custom **Amazon VPC (Virtual Private Cloud)** to create a logically isolated section of the AWS cloud.

* **Database Tier:** The PostgreSQL database was deployed on **AWS RDS (Relational Database Service)**. Crucially, it was placed within a **private subnet**, making it completely inaccessible from the public internet. This prevented direct database attacks and unauthorized access.
* **Application Tier:** The Python/Flask REST API was deployed as a serverless function using **AWS Lambda**. This allowed for automatic scaling and reduced operational overhead.
* **API Exposure:** **Amazon API Gateway** was used as the public-facing entry point for all API requests. This acted as a secure front door, handling traffic management, authentication, and protecting the Lambda function from direct exposure.

### Security Implementation Details

Security was not an afterthought but a core design principle.

*  **Network Isolation:** By using a combination of public and private subnets within the VPC, I ensured that only the necessary components were exposed. The API Gateway resided in the public subnet, while the critical database asset was protected in the private subnet.
*  **Principle of Least Privilege:** I implemented strict access control using **AWS IAM (Identity and Access Management)**. A specific IAM role was created for the Lambda function with a granular policy attached. This policy only granted the function the exact permissions needed to interact with our specific RDS database instance and nothing more, drastically reducing the potential impact of a compromised application layer.
*  **Data Protection:** All data stored in the RDS database and in transit between the API Gateway and Lambda was encrypted using AWS's built-in encryption services.

---

## Technologies Used

* **Cloud Provider:** Amazon Web Services (AWS)
* **Core AWS Services:** VPC, RDS, Lambda, API Gateway, IAM, S3
* **Backend Language:** Python
* **API Framework:** Flask
* **Database:** PostgreSQL
* **Development Concepts:** REST API Design, Serverless Architecture, Cloud Security, Database Normalization, SDLC
