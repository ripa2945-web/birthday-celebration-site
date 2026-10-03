
<div align="center">

# 🛡️ THE CYBERNETIC ECOSYSTEM OF ASTRA MASHRUK BD 🛡️
### *Advanced MITM, Reconnaissance, Exploitation, and Termux Python Utilities*

[![Termux Environment](https://img.shields.io/badge/Termux-Compatible-00FF66?style=for-the-badge&logo=linux&logoColor=black)](https://termux.dev)
[![Python Script](https://img.shields.io/badge/Python-3.x-00F0FF?style=for-the-badge&logo=python&logoColor=black)](https://www.python.org)
[![Security Core](https://img.shields.io/badge/Astra_Mashrukh_BD-Active-FF0055?style=for-the-badge&logo=hackthebox&logoColor=black)](https://github.com)

</div>


## ⚡ Quick Setup in Termux
Run these commands in your Termux terminal to update your environment and install all core packages:

```bash
pkg update && pkg upgrade -y
pkg install python git nmap tshark curl dnsenum hydra -y
pip install --upgrade pip requests scapy mitmproxy

```

---

## 🌐 1. MITM & Network Tools

| Tool Name | Description & Usage | Termux/Linux Command |
| --- | --- | --- |
| **mitmproxy** | Interactive TLS/SSL-intercepting HTTP proxy for debugging and traffic analysis. | `pip install mitmproxy` |
| **tshark** | Command-line network protocol analyzer (CLI version of Wireshark). | `pkg install tshark` |
| **dnsenum** | Multithreaded domain name enumeration tool to find subdomains and DNS records. | `pkg install dnsenum` |
| **macchanger** | Utility for viewing and changing MAC addresses of network interfaces. | `pkg install macchanger` |

---

## 🔍 2. Reconnaissance & OSINT Tools

| Tool Name | Description & Usage | Termux/Linux Command |
| --- | --- | --- |
| **nmap** | Network exploration tool and security / port scanner. | `pkg install nmap` |
| **theHarvester** | Gathers emails, subdomains, hosts, and employee names from public sources. | `git clone https://github.com/laramies/theHarvester` |
| **dirsearch** | Web path scanner / brute-forcer to find hidden directories and files. | `pkg install dirsearch` |
| **sherlock** | Hunt down social media accounts by username across social networks. | `pip install sherlock-project` |

---

## 💥 3. Exploitation & Brute-Force Frameworks

| Tool Name | Description & Usage | Termux/Linux Command |
| --- | --- | --- |
| **Hydra** | Very fast network login cracker supporting numerous protocols (SSH, FTP, HTTP). | `pkg install hydra` |
| **Metasploit** | World-class penetration testing framework for exploit development. | *Requires proot/Ubuntu* |
| **Sqlmap** | Automatic SQL injection and database takeover tool. | `pkg install sqlmap` |

---

## 🐍 4. Custom Python Tool: `AstraRecon-X`

Save this script as `astra_recon.py` in Termux. It provides multi-threaded TCP port scanning and lightweight service discovery via Python standard libraries.

### `astra_recon.py` Code:

```python
#!/usr/bin/env python3
import socket
import sys
import threading
from datetime import datetime

def banner():
    print(r"""
     ___  __  __ ___   ___  ____  
    / _ \|  \/  | _ \ | _ \|  _ \ 
   | (_) | |\/| |  _/ |   /| | | |
    \___/|_|  |_|_|   |_|_\|_| |_|
    [ Astra Mashrukh BD - Termux Core ]
    """)

def scan_port(target_ip, port):
    try:
        s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        s.settimeout(0.8)
        result = s.connect_ex((target_ip, port))
        if result == 0:
            print(f"[+] Port {port:5d} : OPEN")
        s.close()
    except Exception:
        pass

def main():
    banner()
    if len(sys.argv) < 2:
        print("Usage: python3 astra_recon.py <Target-IP>")
        sys.exit(1)
        
    target = sys.argv[1]
    print(f"[*] Target IP: {target}")
    print(f"[*] Scan started at: {str(datetime.now())}")
    print("-" * 40)

    threads = []
    for port in range(1, 1025):
        t = threading.Thread(target=scan_port, args=(target, port))
        threads.append(t)
        t.start()

    for t in threads:
        t.join()

    print("-" * 40)
    print("[✓] Reconnaissance completed successfully.")

if __name__ == '__main__':
    main()

```

### How to Run:

```bash
python3 astra_recon.py 127.0.0.1

```

---
