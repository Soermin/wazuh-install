# Install Wazuh Agent - OS Ubuntu 22.04
Setelah berhasil menginstall Wauzuh Server, maka Wazuh Server tidak lengkap tanpa adanya Agent yang akan dimonitor. Agar Wazuh dapat monitoring terhadap endpoint, setiap endpoint haruslah diinstall Wazuh Agent. Agent ini berfungsi untuk mengumpulkan log, mendeteksi perubahan file dan mengirim data tersebut ke Wazuh Manager untuk dianalisis lebih dalam. Untuk menginstall Wazuh Agent dapat dilakukan dengan menggunakan dua metode yaitu manual dan automasi menggunakan script dari Wazuh.

## Install Manual
Dalam Proses install Wazuh Agent pad endpoint memerlukan akses root untuk menjalankan semua perintah pemasangan. 
### Menambahkan Repositori
Sebelum proses instalasi, haruslah terlebih dahulu membuat repositori untuk Wazuh Agent.
- **Install Kunci GPG**
  ```
  curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | gpg --no-default-keyring --keyring gnupg-ring:/usr/share/keyrings/wazuh.gpg --import && chmod 644 /usr/share/keyrings/wazuh.gpg
  ```
- **Tambahkan Repositori**
  ```
  echo "deb [signed-by=/usr/share/keyrings/wazuh.gpg] https://packages.wazuh.com/4.x/apt/ stable main" | tee -a /etc/apt/sources.list.d/wazuh.list
  ```
- **Update Device**
  ```
  apt-get update
  ```
### Deploy Wazuh Agent 
Setelah repositori telah dibuat, barulah dapat dilakukan instalasi Wazuh Agent di endpoint.
```
WAZUH_MANAGER="<ip_address_wazuh_manager>" apt-get install wazuh-agent
```
Aktifkan dan mulai Wazuh-Agent
```
systemctl daemon-reload
systemctl enable wazuh-agent
systemctl start wazuh-agent
```
Disarankan untuk menonaktifkan update otomatis dari Wazuh Agent untuk menghindari bentrok jika versi Wazuh Agent dan Wazuh Server berbeda. Untuk itu dapat menggunakan perintah berikut :
```
sed -i "s/^deb/#deb/" /etc/apt/sources.list.d/wazuh.list
```



