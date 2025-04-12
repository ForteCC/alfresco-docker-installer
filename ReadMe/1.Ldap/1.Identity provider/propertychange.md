/usr/local/tomcat/shared/classes/alfresco-global.properties

make change in this:
```bash
authentication.chain=ldap1:ldap,alfrescoNtlm1:alfrescoNtlm

ldap.authentication.active=true
ldap.authentication.allowGuestLogin=false
ldap.authentication.userNameFormat=samAccountName=%s,OU=Users,OU=Tap Electric,DC=tapelectric,DC=local

ldap.authentication.java.naming.provider.url=ldap://10.20.102.10:389
ldap.authentication.java.naming.security.authentication=simple
ldap.authentication.java.naming.security.principal=CN=Mitesh Jalan,OU=Users,OU=Tap Electric,DC=tapelectric,DC=local
ldap.authentication.java.naming.security.credentials=ComplexHai@2692000

ldap.synchronization.active=true
ldap.synchronization.userSearchBase=OU=Users,OU=Tap Electric,DC=tapelectric,DC=local
ldap.synchronization.groupSearchBase=OU=Groups,DC=tapelectric,DC=local
ldap.synchronization.userIdAttributeName=samAccountName
ldap.synchronization.groupIdAttributeName=samAccountName

ldap.authentication.defaultAdministratorUserNames=admin

```
---

Making changes in the running Docker container **can be very helpful for testing** purposes, especially if you're **experimenting** with configurations and want to quickly validate if those changes work.

Here’s why and how it can be useful for **testing**:

### Benefits of Making Changes Directly in a Running Docker Container (for testing):
1. **Quick Validation**: It allows you to immediately test changes in the **configuration** (like `alfresco-global.properties`) without needing to rebuild the image or modify `docker-compose.yml`. This can save you time during the trial-and-error phase.
   
2. **Immediate Feedback**: After making the change, you can restart the container, check the logs, and test authentication almost instantly to confirm whether the change works as expected.

3. **No Need for Rebuild**: Instead of rebuilding an image or modifying volumes, you can make real-time adjustments and see the impact directly.

---

### Testing Process After Making Changes in the Running Container:

1. **Verify the Changes**:
   After you edit the `alfresco-global.properties` file, confirm the changes are correct using:
   ```bash
   docker exec -it alfresco-1 cat /usr/local/tomcat/shared/classes/alfresco-global.properties
   ```

2. **Restart the Alfresco Container**:
   Restart the container to apply the changes:
   ```bash
   docker restart alfresco-1
   ```

3. **Check Logs**:
   Review the logs to confirm there are no errors related to the changes, especially LDAP authentication:
   ```bash
   docker logs -f alfresco-1
   ```

4. **Test Authentication**:
   Try logging in with a user from your **LDAP directory** to confirm that the authentication and synchronization settings work as intended.

5. **Test Synchronization**:
   If you also made changes to **LDAP synchronization** settings, check if users are being synchronized correctly.

---

### What to Keep in Mind:
- **Temporary Changes**: Remember, changes made directly inside a running container are **temporary**. If the container stops, the changes will be lost. It’s great for testing, but you’ll want to **persist** them (e.g., using Docker volumes or by committing the container) if you’re satisfied with the results and want them to remain across container restarts.

---

### In Conclusion:
Yes, **modifying the running container** is a **valid and useful approach for testing** changes quickly, especially during configuration or debugging phases. Just ensure you persist the changes (e.g., through volumes or committing the container to an image) once you’re satisfied with the results for long-term use.

Let me know if you need further clarification or if you'd like to proceed with any of the persistence options!



---
## How to check if the ldap configuration is working

```bash
apt update && apt install -y ldap-utils
```
```bash
ldapsearch -H ldap://10.20.102.10:389 \
  -D "CN=Mitesh Jalan,OU=Users,OU=Tap Electric,DC=tapelectric,DC=local" \
  -w "PassWORD" \
  -b "OU=Users,OU=Tap Electric,DC=tapelectric,DC=local" \
  "(sAMAccountName=mjalan)"

```
- This should be able to list the property of user.
- 