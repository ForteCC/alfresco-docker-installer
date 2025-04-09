# Explanation of Alfresco Docker Configuration

## Docker Compose Service (alfresco)

This is a Docker Compose configuration for an Alfresco Content Services (Community Edition) container. Here's what each section does:

### Build Configuration
- Builds from a Dockerfile in the `./alfresco` directory
- Uses build arguments:
  - `ALFRESCO_TAG`: Specifies which Alfresco version to use (from environment variable `ALFRESCO_CE_TAG`)
  - `DB`: Sets the database type to PostgreSQL
  - `SOLR_COMMS`: Configures Solr communication as "secret" (shared secret authentication)

### Resource Limits
- Sets memory limit to 7488MB (7.5GB)

### Dependencies
- Depends on:
  - `alfresco-identity-service` (must be started first)
  - `postgres` database (must be healthy before starting)

### Environment Variables
- **JAVA_TOOL_OPTIONS**: Configures encryption settings for Alfresco
  - Uses JCEKS keystore type with DESede encryption
  - Specifies keystore location and passwords
- **JAVA_OPTS**: Main Alfresco configuration options including:
  - Database connection details (PostgreSQL)
  - Admin password (bcrypt hashed)
  - Solr search configuration
  - Host and port settings
  - Transform service URLs
  - Memory management (G1GC with 50-80% RAM usage)
  - Disabled CSRF protection for development
  - Commented out LDAP/AD integration configuration

### Healthcheck
- Checks Alfresco readiness by hitting the `/alfresco/api/-default-/public/alfresco/versions/1/probes/-ready-` endpoint
- Checks every 30 seconds with 3 retries

### Volumes
- Maps host directories for:
  - Alfresco data (`./data/alf-repo-data`)
  - Logs (`./logs/alfresco`)

## Dockerfile Explanation

This Dockerfile builds a custom Alfresco Content Repository image:

### Base Image
- Uses `alfresco/alfresco-content-repository-community` with version specified by `ALFRESCO_TAG`

### Configuration
1. **User Context**: Switches to root to install components
2. **Module Installation**:
   - Copies AMPs (Alfresco Module Packages) to Tomcat's amps directory
   - Copies JAR files to Alfresco's lib directory
   - Installs AMPs using Alfresco Module Management Tool (MMT)
3. **Database Configuration**:
   - Sets up MySQL/MariaDB JDBC driver if DB type is "mariadb"
   - Updates yum repositories for package installation
4. **Solr Communication**:
   - Configures SSL communication if `SOLR_COMMS` is "https"
   - Modifies Tomcat's server.xml to add HTTPS connector
   - Uses provided keystore/truststore configurations

### Key Points
- The image is customized with additional modules and database drivers
- SSL configuration is optional based on the `SOLR_COMMS` parameter
- Maintains Alfresco's default security model while allowing customization
- Designed to work with PostgreSQL by default (as specified in the compose file)

This configuration provides a complete Alfresco Content Services deployment with search (Solr), database (PostgreSQL), and optional LDAP integration, suitable for development or production use with proper security adjustments.