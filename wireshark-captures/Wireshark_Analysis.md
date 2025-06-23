# 📊 Wireshark Analysis Notes

This document summarizes the key findings from the Wireshark capture during the Nmap port scanning process on the target `192.168.1.4`.

---

##  Interface & Capture Setup

- **Interface used**: `eth0`
- **Source system (attacker)**: `192.168.1.5` (Kali)
- **Target system (victim)**: `192.168.1.4` (Metasploitable2)
- **Capture tool**: Wireshark
- **Total packets captured**: 2029

---

##  Observations

### 1. **ARP Requests**
- Initial ARP broadcasts detected (lines 1–2).
- Attacker system requesting MAC address of target (192.168.1.4).

### 2. **DNS Resolution**
- A DNS PTR request to `192.168.1.4` by attacker.
- Response: `No such name`, meaning no reverse DNS entry.

### 3. **TCP Port Scan Signatures**
- Multiple TCP packets from `192.168.1.5` to various ports on `192.168.1.4`.
- Format: `SYN` packets sent from random high ports → open ports (e.g., 445).
- Response:
  - If port is **open**, target replies with `SYN, ACK`.
  - If port is **closed**, response is typically `RST`.

### 4. **Highlighted Pattern**
- Many repeated `SYN` and `SYN, ACK` sequences.
- Wireshark displays this as a typical **TCP SYN scan** (consistent with `nmap -sS`).

---

##  Notable Packet Example

- **Packet**: 1609  
- **Src IP**: `192.168.1.5`  
- **Dst IP**: `192.168.1.4`  
- **Protocol**: TCP  
- **Src Port**: 51103  
- **Dst Port**: 63924  
- **Flags**: SYN, ACK  
- **Payload**: 60 bytes

---

##  Insights

- This packet flow confirms the behavior of a stealth scan (TCP half-open scan).
- No full TCP handshakes were completed.
- This helps the attacker remain less detectable by intrusion detection systems (IDS).

---

##  Recommendations

- Use a firewall to limit external access to unnecessary ports.
- Deploy IDS/IPS to monitor unusual SYN traffic.
- Regularly review ARP and DNS logs for unusual queries.
- Use Wireshark filters like:
  - `ip.addr == 192.168.1.4`
  - `tcp.flags.syn == 1 and tcp.flags.ack == 0`

---

📝 **File Captured**: `wireshark_eth0MPPF82.pcapng`  
🖼️ **Screenshot**: `wireshark_screenshot.png`
