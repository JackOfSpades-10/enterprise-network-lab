## Screenshot 1 — Interface Assignments

**Path:** Interfaces → Assignments  

**Description:**  
Interface layout showing pfSense configured with multiple VLAN-backed interfaces. WAN is isolated, while management (VLAN 10), users (VLAN 30), and guest (VLAN 20) networks are mapped as separate firewall interfaces to enable policy-based segmentation.

![Screenshot 1 – Interface Assignments](images/Screenshot%201.png)

---

## Screenshot 2 — VLAN Configuration

**Path:** Interfaces → VLANs  

**Description:**  
Defined VLANs used to segment management, user, and guest traffic over a shared physical interface. Each VLAN is tagged on the LAN interface to support trunking to downstream switches and wireless access points.

![Screenshot 2 – VLAN Configuration](images/Screenshot%202.png)

---

## Screenshot 3 — Guest Firewall Rules

**Path:** Firewall → Rules → GUEST  

**Description:**  
Interface-based firewall rules enforcing network isolation. Guest traffic is explicitly blocked from accessing management and user networks while still being permitted outbound internet access.

![Screenshot 3 – Guest Firewall Rules](images/Screenshot%203.png)

---

## Screenshot 4 — DHCP Server Scopes

**Path:** Services → DHCP Server  

**Description:**  
Independent DHCP scopes per VLAN, allowing each network segment to dynamically assign addresses within its own subnet while maintaining isolation between roles.

![Screenshot 4 – DHCP Server Scopes](images/Screenshot%204.png)

---

## Screenshot 5 — pfSense Dashboard

**Path:** Status → Dashboard  

**Description:**  
Operational dashboard displaying live interface status, gateway health, traffic graphs, and system resource utilization for ongoing monitoring of the firewall environment.

![Screenshot 5 – pfSense Dashboard](images/Screenshot%205.png)
