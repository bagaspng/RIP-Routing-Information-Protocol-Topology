
# RIP (Routing Information Protocol) Topology Simulation

🌐 **Simulasi Jaringan Komputer dengan Routing Dinamis menggunakan RIP versi 2**
<img width="641" height="526" alt="image" src="https://github.com/user-attachments/assets/fa85fc42-bcda-4938-bced-556405923d06" />

## 🧩 Deskripsi Project

Project ini merupakan implementasi simulasi jaringan komputer menggunakan **Cisco Packet Tracer** dengan menerapkan protokol routing dinamis **RIP (Routing Information Protocol) versi 2**. 
Simulasi ini mendemonstrasikan bagaimana router dapat secara otomatis mempelajari dan berbagi informasi routing untuk memungkinkan komunikasi antar jaringan yang berbeda.

## 🎯 Tujuan Project

- Mengimplementasikan routing dinamis menggunakan protokol RIP v2
- Memungkinkan komunikasi antar PC di jaringan yang berbeda
- Memahami konsep convergence pada routing dinamis
- Mempelajari konfigurasi RIP pada router Cisco

## 🗺️ Topologi Jaringan

### Arsitektur
```
Router1 ←→ Router2 ←→ Router3
   ↓          ↓          ↓
Switch1    Switch2    Switch3
   ↓          ↓          ↓
PC0-PC1    PC2-PC3    PC4-PC5
```

### Detail Konfigurasi

| Router  | LAN Network      | Gateway IP    | Interface |
|---------|------------------|---------------|-----------|
| Router1 | 192.168.11.0/24  | 192.168.11.1  | Fa0/0     |
| Router2 | 192.168.21.0/24  | 192.168.21.1  | Fa0/0     |
| Router3 | 192.168.31.0/24  | 192.168.31.1  | Fa0/0     |

### Koneksi Antar Router (Serial Links)

| Koneksi | Interface Router1 | Interface Router2 | Interface Router3 |
|---------|-------------------|-------------------|-------------------|
| R1-R2   | Se2/0             | Se2/0             | -                 |
| R2-R3   | -                 | Se3/0             | Se2/0             |

## 🔧 Komponen Jaringan

- **3 Router Cisco** (dengan interface FastEthernet dan Serial)
- **3 Switch** (menghubungkan router ke PC)
- **6 PC** (2 PC per LAN segment)
- **Kabel Serial** (koneksi antar router)
- **Kabel Straight-through** (koneksi PC ke switch dan router ke switch)

## ⚙️ Konfigurasi RIP

### Konfigurasi Dasar Router
```cisco
Router> enable
Router# configure terminal
Router(config)# router rip
Router(config-router)# version 2
Router(config-router)# network [network_address]
Router(config-router)# no auto-summary
```

## 🚀 Cara Menjalankan

1. **Buka Cisco Packet Tracer**
2. **Load file topology** (. pkt file)
3. **Verifikasi konfigurasi** pada setiap router
4. **Test konektivitas** dengan ping antar PC
5. **Monitor routing table** menggunakan `show ip route`

## 🧪 Testing & Verifikasi

### Command untuk Verifikasi
```cisco
# Melihat routing table
show ip route

# Melihat konfigurasi RIP
show ip protocols

# Test konektivitas
ping [destination_ip]

# Debug RIP (opsional)
debug ip rip
```

### Test Scenario
- **Ping dari PC0 ke PC2**: `192.168.11.10` → `192.168.21.10`
- **Ping dari PC1 ke PC5**: `192.168.11.11` → `192.168.31.11`
- **Ping dari PC3 ke PC4**: `192.168.21.11` → `192.168.31.10`

## 📊 Expected Results

✅ **Semua PC dapat saling ping**  
✅ **Routing table terisi otomatis**  
✅ **Network convergence tercapai**  
✅ **RIP updates berjalan setiap 30 detik**  

## 🔍 Troubleshooting

| Masalah | Solusi |
|---------|--------|
| PC tidak bisa ping ke jaringan lain | Periksa konfigurasi RIP dan IP addressing |
| Routing table kosong | Pastikan RIP version 2 dan network sudah dikonfigurasi |
| Serial link down | Periksa konfigurasi interface dan clock rate |

## 📚 Konsep yang Dipelajari

- **Distance Vector Routing Protocol**
- **RIP Metrics (Hop Count)**
- **Split Horizon**
- **Route Poisoning**
- **Hold-down Timer**
- **Network Convergence**

## 📁 File Structure

```
RIP-Routing-Information-Protocol-Topology/
├── README.md
├── topology.pkt          # File Cisco Packet Tracer
├── docs/
│   ├── configuration.md  # Detail konfigurasi
│   └── troubleshooting.md
└── images/
    └── topology-diagram.png
```

## 🤝 Kontribusi

Silakan buat pull request untuk perbaikan atau penambahan fitur. Pastikan untuk:
- Menguji konfigurasi pada Cisco Packet Tracer
- Mendokumentasikan perubahan yang dibuat
- Mengikuti standar konfigurasi Cisco

## 📖 Referensi

- [Cisco RIP Configuration Guide](https://www.cisco.com/c/en/us/tech/ip/routing-information-protocol-rip/index.html)
- [RIP Protocol RFC 2453](https://tools.ietf.org/html/rfc2453)

---

**Dibuat menggunakan Cisco Packet Tracer**  
**Protokol**:  RIP v2 | **Topology**: Linear | **Devices**: 3 Routers, 3 Switches, 6 PCs
