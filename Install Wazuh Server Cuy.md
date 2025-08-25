# Install Wazuh Server - OS Ubuntu 22.04

Wazuh provides an installation assistant that simplifies the process of installing server components, including the Wazuh Manager, Elasticsearch, and the Wazuh Dashboard.

## 1. Download and Run the Wazuh Installation Assistant
```
curl -sO https://packages.wazuh.com/4.12/wazuh-install.sh && sudo bash ./wazuh-install.sh -a
```
## 2. Wait for the Installation Process
The script will automatically:
- Check the system and install dependencies
- Install all required components
- Configure basic settings  

The installation time depends on the internet connection and system specifications (usually 5–15 minutes).

## 3. Access User & Password
After the installation is complete, Wazuh will output the user and password needed to log in to the Wazuh Dashboard:
```
INFO: --- Summary ---
INFO: You can access the web interface https://<WAZUH_DASHBOARD_IP_ADDRESS>
    User: admin
    Password: <ADMIN_PASSWORD>
INFO: Installation finished.
```
If you forget the password, it can be found in the file _wazuh-password.txt_ inside _wazuh-install-files.tar_. Use the following command:
```
sudo tar -O -xvf wazuh-install-files.tar wazuh-install-files/wazuh-passwords.txt
```

## 4. Access the Wazuh Dashboard
Open your browser and access it via:

```
https://<ip-address-wazuh-server>
```

## 💡 Additional Tips
After successfully installing Wazuh, you can change the default credential password using the following command:
```
/usr/share/wazuh-dashboard/plugins/wazuh/wazuh-passwords-tool.sh
```




