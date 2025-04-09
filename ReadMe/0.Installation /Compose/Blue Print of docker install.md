# List of image used:

1. **alfresco/alfresco-share:25.1.0**

2. **alfresco/alfresco-transform-core-aio:5.1.7**

3. **traefik:3.1**

4. **alfresco/alfresco-activemq:5.18-jre17-rockylinux8**

5. **quay.io/alfresco/alfresco-control-center:9.4.0**

6. **postgres:14.4**

7. **alfresco/alfresco-search-services:2.0.15**

8. **alfresco/alfresco-content-repository-community:25.1.0**

9. **alfresco/alfresco-content-app:6.0.0**

---

1. Alfresco-share(`alfresco/alfresco-share:25.1.0`):
- A frontend web application for Alfresco Content Services (ACS).

- Provides a user interface for document management, collaboration, and workflow.

- Runs on Apache Tomcat and typically communicates with the Alfresco backend.
2. **Alfresco Transform Core AIO (`alfresco/alfresco-transform-core-aio:5.1.7`)**
- Responsible for transforming documents into different formats (e.g., PDF, images, text extraction).

- Uses libraries like LibreOffice, ImageMagick, and Tika.

- Exposes an API that ACS calls for transformations.
3. **Traefik (`traefik:3.1`)**
- A reverse proxy and load balancer.

- Manages traffic to various Alfresco services.

- Provides routing, SSL termination, and monitoring.
4. **Alfresco ActiveMQ (`alfresco/alfresco-activemq:5.18-jre17-rockylinux8`)**
- A message broker based on Apache ActiveMQ.

- Handles asynchronous messaging and event-driven communication between Alfresco services.

- Used for tasks like indexing, transformations, and workflow processing.
5. **Alfresco Control Center (`quay.io/alfresco/alfresco-control-center:9.4.0`)**
- A monitoring and management tool for Alfresco services.

- Allows administrators to track service health, logs, and configurations.
6. **PostgreSQL (`postgres:14.4`)**
- The relational database management system (RDBMS) used by Alfresco.

- Stores metadata, user information, and repository configurations.
7. **Alfresco Search Services (`alfresco/alfresco-search-services:2.0.15`)**
- Powered by Apache Solr.

- Indexes documents stored in Alfresco for fast searching.

- Provides full-text search and filtering.
8. **Alfresco Content Repository (`alfresco/alfresco-content-repository-community:25.1.0`)**
- The core backend service of Alfresco Content Services.

- Manages document storage, permissions, workflows, and metadata.

- Exposes a REST API for integrations.

- Image package: [Alfresco/acs-community-packaging: Packaging of Docker containers, war file and zip for Alfresco Content Services (Community)](https://github.com/Alfresco/acs-community-packaging)

- Build own: [Alfresco/acs-community-pa10ckaging: Packaging of Docker containers, war file and zip for Alfresco Content Services (Community)](https://github.com/Alfresco/acs-community-packaging)
9. **Alfresco Content App (`alfresco/alfresco-content-app:6.0.0`)**
- A modern web client for interacting with Alfresco repositories.

- Built with Angular, offering an alternative UI to Alfresco Share.

- Provides a responsive and user-friendly interface for content management.

---
