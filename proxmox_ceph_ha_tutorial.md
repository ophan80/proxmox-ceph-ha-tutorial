# 🔥 High Availability Cluster dengan Proxmox & Ceph + Monitoring 🚀

## 📌 Pendahuluan
Tutorial ini menjelaskan **cara membangun cluster Proxmox dengan High Availability (HA) & Ceph sebagai storage bersama**, serta **monitoring dengan Grafana & Alerting ke Telegram**.

---

# **📌 Bagian 1: Instalasi & Konfigurasi Cluster Proxmox**
```bash
pvecm create prox-cluster
pvecm add 10.10.10.1
pvecm status
```

---

# **📌 Bagian 2: Setup Ceph Storage untuk Cluster**
```bash
apt install ceph ceph-common -y
pveceph init --network 10.10.10.0/24
pveceph osd create /dev/sdb
ceph -s
```

---

# **📌 Bagian 3: Konfigurasi High Availability (HA) & Live Migration**
```bash
ha-manager add group prox-ha-group
ha-manager add vm 100 --group prox-ha-group
poweroff -f
ha-manager status
```

---

# **📌 Bagian 4: Install Grafana & Prometheus untuk Monitoring Proxmox**
```bash
apt install grafana prometheus prometheus-node-exporter -y
systemctl enable grafana-server prometheus
systemctl start grafana-server prometheus
```

---

# **📌 Bagian 5: Monitoring Ceph Storage dengan Grafana**
```bash
apt install ceph-mgr prometheus-ceph-exporter -y
ceph mgr module enable prometheus
systemctl restart prometheus
```

---

# **📌 Bagian 6: Setup Notifikasi Telegram jika Node Down atau Storage Penuh**
```bash
nano /etc/grafana/telegram-notify.sh
nohup bash /etc/grafana/telegram-notify.sh &
```

---

## 🔥 **Kesimpulan**
✅ **Cluster Proxmox dengan HA & Live Migration siap digunakan**  
✅ **Ceph sebagai shared storage untuk failover otomatis**  
✅ **Grafana Dashboard untuk monitoring cluster & storage**  
✅ **Notifikasi Telegram jika ada masalah di cluster**  

🚀 **Siap diupload ke GitHub!**  
