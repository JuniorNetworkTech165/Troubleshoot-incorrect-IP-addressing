# 3rd Lab: Troubleshoot incorrect IP addressing.

This lab demonstrate how to identify, troubleshoot, and fix IP addressing misconfiguration in a Local Area Network (LAN).

## Tools & Environment.
* **Emulation Software: GNS3**
* **Device: 3x VPCS, 1x Ethernet switch** 

---

**The table below shows the initial network configuration, which were recorded during the lab setup.**

## 1. Initial Addressing table.

|   Device   |  IP Address        |   Subnet Mask     |
|   :---     |  :---              |   :---            |
|   **PC1**  |  `192.168.20.10`   |   `255.255.255.0` |
|   **PC2**  |  `192.168.20.11`   |   `255.255.255.0` |
|   **PC3**  |  `192.168.30.12`   |   `255.255.255.0` |

### Network topology.
![Network Topology](https://github.com/JuniorNetworkTech165/Troubleshoot-incorrect-IP-addressing/blob/main/Network%20topology.png?raw=true)

---

## 2. Problem Statement.

* **PC1**  and **PC2** are configured on the same `192.168.20.0/24` network.

* **PC3** was deliberately misconfigured on the `192.168.30.0/24` network.

* **Result:** Ping requests sent from **PC1** or **PC2** to **PC3** failed, because **PC3** did not belong to the same `192.168.20.0/24` network.

---

## 3. Troubleshooting & Solutions.

1. **Diagnosis:** I tried to ping **PC3** (`192.168.30.12`) from **PC1** and **PC2**, but the connection timed out, because **PC3** did not belong to the same `192.168.20.0/24` network.

2. **Fix:** I corrected **PC3**'s IP configuration, so that it can belong to the same `192.168.20.0/24` network as **PC1** and **PC2**.

### Corrected Addressing Table.

|  Device   |  IP Address      |  Subnet Mask     |  Status   |
|  :---     |  :---            |  :---            |  :---     |
|  **PC1**  |  `192.168.20.10` |  `255.255.255.0` |  Active   |
|  **PC2**  |  `192.168.20.11` |  `255.255.255.0` |  Active   |
|  **PC3**  |  `192.168.20.12` |  `255.255.255.0` | **Fixed** |

---

## 4. Testing and verification.

* I ran the command `ping 192.168.20.12` from both **PC1** and **PC2**.
* **Results:** The ping test was successful! All ping packets were received with zero packet loss, confirming that all computers can talk to each other.
