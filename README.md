

# Communication-Networks

   name : SenthilKumar K
   reg no: 212222060234

## Step 1: Configure VLANs on Layer 3 Switch

Enter global configuration mode:

Switch> enable
Switch# configure terminal


Create VLANs:

Switch(config)# vlan 10
Switch(config-vlan)# name Sales
Switch(config-vlan)# exit

Switch(config)# vlan 20
Switch(config-vlan)# name Marketing
Switch(config-vlan)# exit

## Step 2: Assign Ports to VLANs

Assign PCs to VLAN 10 and VLAN 20:

Switch(config)# interface range fa0/1 - 2
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 10
Switch(config-if-range)# exit

Switch(config)# interface range fa0/3 - 4
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 20
Switch(config-if-range)# exit

## Step 3: Configure Trunk Port to Layer 2 Switch (if used)
Switch(config)# interface fa0/24
Switch(config-if)# switchport mode trunk
Switch(config-if)# exit


This allows multiple VLAN traffic to pass between switches.

## Step 4: Create SVIs (Virtual Interfaces) on Layer 3 Switch

Assign IP addresses for VLAN gateways:

Switch(config)# interface vlan 10
Switch(config-if)# ip address 10.1.1.1 255.255.255.0
Switch(config-if)# no shutdown
Switch(config-if)# exit

Switch(config)# interface vlan 20
Switch(config-if)# ip address 20.1.1.1 255.255.255.0
Switch(config-if)# no shutdown
Switch(config-if)# exit

## Step 5: Enable Routing on Layer 3 Switch
Switch(config)# ip routing

## Step 6: Configure PCs’ IP and Default Gateway

PC0 and PC2 (VLAN 10):

IP: 10.1.1.100
Subnet: 255.255.255.0
Default Gateway: 10.1.1.1


PC1 and PC3 (VLAN 20):

IP: 20.1.1.100
Subnet: 255.255.255.0
Default Gateway: 20.1.1.1

## Step 7: Test Connectivity

Open PC0 → Command Prompt → ping 20.1.1.100 (PC1).

If everything is configured correctly, you should get replies. ✅



## output : 
<img width="1847" height="825" alt="cn" src="https://github.com/user-attachments/assets/e11e2a5b-5a9b-4891-a577-6160c9411530" />

## Conclusion: Inter-VLAN Routing

Problem Solved: VLANs are isolated by default, preventing communication between devices in different VLANs.

Solution: A Layer 3 switch allows seamless communication by performing routing between VLANs internally.



Takeaway: Layer 3 switches combine switching and routing in a single device, making Inter-VLAN communication fast, scalable, and easy to manage.
