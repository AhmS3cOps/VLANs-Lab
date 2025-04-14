
# **VLANs Lab**

## **Description**  
This project demonstrates the creation of VLANs in Cisco Packet Tracer, utilizing trunking to enable inter-switch communication.

---

## **Languages and Utilities Used**
- **Cisco Packet Tracer**: Network simulation tool.
- **TCP/IP Protocol Suite**: Networking standards for communication.
- **Command Line Interface (CLI)**: For router and switch configuration.

## **Environments Used**
- **Windows 11**: Operating system for running Cisco Packet Tracer.

---

## **Program Walk-through**

### **Instructions**

Configure the network as follows:

1. **3650 Layer 3 Switch** — IP addresses and interVLAN routing:
   - VLAN 1: `10.1.1.254/24`
   - VLAN 10: `10.1.10.254/24`
   - VLAN 20: `10.1.20.254/24`
   - VLAN 30: `10.1.30.254/24`
   - VLAN 100: `10.1.100.254/24`

2. **Access Layer Switches** — management IP addresses in VLAN 1:
   - Switch 1: `10.1.1.1/24`
   - Switch 2: `10.1.1.2/24`
   - Switch 3: `10.1.1.3/24`

3. **Access Ports Configuration:**
   - PC1: VLAN 10 — `10.1.10.10/24`
   - PC2: VLAN 20 — `10.1.20.20/24`
   - PC3: VLAN 30 — `10.1.30.30/24`
   - Server1: VLAN 100 — `10.1.100.100/24`

4. **Switch Connections:**
   - Configure ports between switches as trunk ports.

5. **Testing:**
   - Ensure all PCs and the server can ping each other.
   - Verify switches can ping the PCs and server.

---

### **1. Initial Setup**

The initial topology consists of switches and PCs:

<p align="center">
  <img src="https://imgur.com/H7WHfR0.png" width="80%" alt="Initial Setup"/>
</p>

---

### **2. Configuring the Switch using CLI**

#### **VLAN Configuration**

Create VLANs 10, 20, 30, and 100 on the Layer 3 switch, assigning IP addresses and subnet masks as specified.

<p align="center">
  <img src="https://imgur.com/bHgGepd.png" width="80%" alt="VLAN Setup"/>
  <img src="https://imgur.com/1ZpW6gY.png" width="80%" alt="VLAN Setup"/>
</p>

#### **Confirming VLAN Creation**

<p align="center">
  <img src="https://imgur.com/mzZxkA6.png" width="80%" alt="VLAN Confirmation"/>
</p>

#### **Setting Up Interfaces**

- **Server Port (Access Port)**
  
<p align="center">
  <img src="https://imgur.com/yPzmbBu.png" width="80%" alt="Access Port Configuration"/>
</p>

- **Switch Trunk Ports**

<p align="center">
  <img src="https://imgur.com/yAGCuux.png" width="80%" alt="Trunk Port Configuration"/>
</p>

Check configuration using:
```plaintext
show run
```

<p align="center">
  <img src="https://imgur.com/idtzqGD.png" width="80%" alt="Show Run Command"/>
  <img src="https://imgur.com/OM5moKN.png" width="80%" alt="Show Run Command"/>
</p>

#### **Configuring VTP (VLAN Trunking Protocol)**

1. Check existing VTP domain:
   ```plaintext
   show vtp status
   ```

2. Set up a new domain:
   ```plaintext
   configure terminal
   vtp domain ccna
   ```

<p align="center">
  <img src="https://imgur.com/j2q5uaK.png" width="80%" alt="VTP Configuration"/>
  <img src="https://imgur.com/UKoDHOv.png" width="80%" alt="VTP Configuration"/>
</p>

#### **Enable IP Routing**

<p align="center">
  <img src="https://imgur.com/cZr9g7V.png" width="80%" alt="Enable IP Routing"/>
</p>

---

### **3. Configuring Layer 2 Switches**

- Set IP addresses and subnet masks under VLAN 1.
- Configure `g0/1` as trunk port and `f0/1` as access port.
- Set default gateway to VLAN 1 IP of Layer 3 switch.

<p align="center">
  <img src="https://imgur.com/mMHNfQO.png" width="80%" alt="Layer 2 Switch Configuration"/>
  <img src="https://imgur.com/fH4T7Ma.png" width="80%" alt="Layer 2 Switch Configuration"/>
</p>

Repeat these steps for the remaining switches.

---

### **4. Configuring PCs and Server**

Manually configure IP settings on each PC and Server.

<p align="center">
  <strong>PC1:</strong><br/>
  <img src="https://imgur.com/ynzenXY.png" width="80%" alt="PC1 Config"/><br/><br/>

  <strong>PC2:</strong><br/>
  <img src="https://imgur.com/qMhfYNb.png" width="80%" alt="PC2 Config"/><br/><br/>

  <strong>PC3:</strong><br/>
  <img src="https://imgur.com/gyZjloG.png" width="80%" alt="PC3 Config"/><br/><br/>

  <strong>Server:</strong><br/>
  <img src="https://imgur.com/rGkcJdv.png" width="80%" alt="Server Config"/>
</p>

---

### **5. Running the Simulation**

To test configurations, ping PCs and the server to verify connectivity.
Ping from PC1 to PC3 and Switch3
<p align="center">
<img src="https://imgur.com/rjsdiJU.png" height="80%" width="80%" alt="Router Configuration"/>
</p>

Ping from Switch3 to PC1, PC2 and PC3
<p align="center">
<img src="https://imgur.com/wFr3qpO.png" height="80%" width="80%" alt="Router Configuration"/>
</p>
---

## ✅ **Conclusion**

The network was successfully configured. All VLANs communicate as expected, and inter-switch communication works via trunking and IP routing.
