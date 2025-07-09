# Install Wazuh Server - OS Ubuntu 22.04

Wazuh menyediakan installation assistant yang menyederhanakan proses instalasi komponen server, termasuk Wazuh Manager, Elasticsearch dan Wazuh Dashboard.

## 1. Unduh dan jalankan wazuh installation assistant
```
curl -sO https://packages.wazuh.com/4.12/wazuh-install.sh && sudo bash ./wazuh-install.sh -a
```
## 2. Tunggu Proses Instalasi
Script tersebut akan langsung otomatis :
- Memeriksa sistem dan melakukan depedensi
- Menginstal semua komponen
- Mengatur Konfigurasi dasar
Waktu instalasi tergantung koneksi internet dan spesifikasi sistem (Biasanya 5-15 menit).

## 3. Akses User & Password
Setelah instalasi selesai, wazuh akan menghasilkan output berupa user dan password yang nantinya diperlukan untuk login ke Wazuh-Dashboard. 
```
INFO: --- Summary ---
INFO: You can access the web interface https://<WAZUH_DASHBOARD_IP_ADDRESS>
    User: admin
    Password: <ADMIN_PASSWORD>
INFO: Installation finished.
```
Kita bisa mnecari password, jika seandainya anda lupa di file _wazuh-password.txt_ yang ada didalam _wazuh-install-files.tar_. Dapat menggunakan perintah berikut :
```
sudo tar -O -xvf wazuh-install-files.tar wazuh-install-files/wazuh-passwords.txt
```

## 4. Akses Wazuh Dashboard 
Buka browser dan akses melalui :
```
https://<ip-address-wazuh-server>
```



