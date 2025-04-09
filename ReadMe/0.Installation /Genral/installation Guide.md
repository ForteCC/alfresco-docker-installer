# What to choose

1. tag 6.0.0-ga  9eneraly (availablle)
this is the final releases and we use this as this are stable.
2. alfresco-community-packaging:
   - how this docker images are produced.
   - here we have the dockerFiles.
   - we need different services.
   - look in the Alfresco/acs-deployment : 
     - in this we have docker-compose/community-docker-compose.yml.
     - this has the complete list of different docker images needed to deploy different images.
     - this project thought dont have persistant storage so there is another project.
   - alfresco-docker-installer.
     - allow custom docker compose with feature like networking, volumes, add-ons etc.
- make the tmp folder where we will install the alfresco.
- Add-ons
  - hub.alfresco
  - this has the add-on services of the alfresco.
- IN UBUNTU: this is permissin issue
  - we do chown of dir. its present in the docker installer repository what to add.



