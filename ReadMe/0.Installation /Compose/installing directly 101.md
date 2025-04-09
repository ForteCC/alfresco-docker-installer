# Installation of app without config changes.



? What HTTP port do you want to use (all the services are using the same port)? 80

? Do you want to specify a custom binding IP for HTTP? No

? Do you want to use FTP (port 2121)? No  

? Do you want to use MariaDB instead of PostgreSQL? No

? Are you using different languages (this is the most common scenario)? Yes

? Do you want to search in the content of the documents? Yes

? Would you like to use Shared Secret or HTTPs for Alfresco-SOLR communication? secret

? Do you want to use the Events service (ActiveMQ)? Yes

? Do you want to use credentials for Events service (ActiveMQ)? No

? Do you want to create an internal SMTP server? No

? Do you want to create an internal LDAP server? No

? Select the addons to be installed: [your choices]

? Do you want Docker to manage volume storage (recommended when dealing with permission issues)? No  ← IMPORTANT CHANGE

? Do you want to use a start script? Yes  

? Do you want to get the script to create host volumes? Yes  ← IMPORTANT CHANGE
