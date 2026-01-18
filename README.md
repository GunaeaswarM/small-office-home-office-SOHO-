# small-office-home-office-SOHO-
This SOHO network uses one switch and one router with four PCs divided into two VLANs. PC1 and PC3 are in VLAN 10, while PC2 and PC4 are in VLAN 20. The switch separates traffic, and the router enables inter-VLAN communication, improving security and performance in a small network.

Switch:
hostname Switch
interface FastEthernet0/1
 switchport access vlan 10
 switchport mode access

interface FastEthernet0/2
 switchport access vlan 10
 switchport mode access

interface FastEthernet0/3
 switchport access vlan 20
 switchport mode access

interface FastEthernet0/4
 switchport access vlan 20
 switchport mode access
interface GigabitEthernet0/1
 switchport mode trunk
!
interface GigabitEthernet0/2
!
interface Vlan1
 no ip address
 shutdown

interface Vlan10
 no ip address

line con 0

line vty 0 4
 login
line vty 5 15
 login
!
!
!
!
end

Router:

hostname Router
interface GigabitEthernet0/0
 no ip address
 duplex auto
 speed auto
!
interface GigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0
!
interface GigabitEthernet0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0
!
interface GigabitEthernet0/1
 no ip address
 duplex auto
 speed auto
 shutdown
!
interface Vlan1
 no ip address
 shutdown
!
ip classless
!
ip flow-export version 9
!
!
!
!
!
!
!
line con 0
!
line aux 0
!
line vty 0 4
 login
!
!
!
end

PC0:
ip address:102.168.10.2
subnet mask: 255.255.255.0
default gateway:192.168.10.1

PC1:

ip address:192.168.10.3
subnet mask:255.255.255.0
default gateway: 192.168.10.1

PC3:
ip address:192.168.20.3
subnet mask:255.255.255.0
default gateway: 192.168.20.1

PC4:
ip address: 192.168.20.2
subnet mask: 255.255.255.0
default gateway:192.168.20.1


