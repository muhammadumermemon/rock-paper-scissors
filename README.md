# Simple Firewall

This repository contains a basic firewall implemented in Python using the `scapy` library. The firewall captures network packets and filters them based on predefined rules, such as allowed IP addresses and blocked ports.

## Requirements

- Python 3.x
- `scapy` library

## Installation

1. **Clone the repository:**

    ```bash
    git clone https://github.com/your-username/simple-firewall.git
    cd simple-firewall
    ```

2. **Install the `scapy` library:**

    ```bash
    pip install scapy
    ```

## Usage

1. **Run the firewall:**

    Execute the script using Python:

    ```bash
    python simple_firewall.py
    ```

2. **Functionality:**

    - The script will capture network packets.
    - It will filter packets based on allowed IP addresses and blocked ports.
    - Blocked packets will be logged and displayed.

## Example

Here's an example of how the firewall works:

```python
from scapy.all import sniff, IP, TCP

# Define allowed IPs and blocked ports
ALLOWED_IPS = ['192.168.1.1', '192.168.1.2']
BLOCKED_PORTS = [80, 443]

# Callback function to process each packet
def packet_callback(packet):
    if packet.haslayer(IP):
        ip_src = packet[IP].src
        if ip_src not in ALLOWED_IPS:
            print(f"Blocked packet from {ip_src}")
            return
    if packet.haslayer(TCP):
        port = packet[TCP].dport
        if port in BLOCKED_PORTS:
            print(f"Blocked packet to port {port}")
            return
    print(packet.show())

# Start sniffing packets
sniff(prn=packet_callback, store=0)
