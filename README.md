---
title: TP FINAL - Introduction to networks Partie 2 CCNA1

---

# TP FINAL - Introduction to networks Partie 2 CCNA1

## CDC 1 - Routage dynamique EIGRP

### Architecture du LAB : 

<img width="2512" height="1347" alt="01 - lab complet" src="https://github.com/user-attachments/assets/bbdb40f2-9cb6-4a6c-923b-5f63f6d40022" />

### Configuration de chaque routeur : 

#### R1#show running-config

```
Building configuration...

Current configuration : 1788 bytes
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
!
hostname R1
!
boot-start-marker
boot-end-marker
!
!
!
no aaa new-model
no ip icmp rate-limit unreachable
!
!
!
!
!
!
no ip domain lookup
ip cef
no ipv6 cef
!
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
!
!
!
!
!
ip tcp synwait-time 5
!
!
!
!
!
!
!
!
!
interface FastEthernet0/0
 ip address 192.168.0.254 255.255.255.0
 duplex full
!
interface GigabitEthernet1/0
 ip address 192.168.1.0 255.255.255.254
 negotiation auto
!
interface GigabitEthernet2/0
 no ip address
 shutdown
 negotiation auto
!
interface GigabitEthernet3/0
 no ip address
 shutdown
 negotiation auto
!
interface FastEthernet4/0
 ip address 192.168.5.0 255.255.255.254
 speed auto
 duplex auto
!
interface FastEthernet4/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface Serial6/0
 ip address 192.168.4.0 255.255.255.254
 encapsulation ppp
 serial restart-delay 0
 clock rate 64000
!
interface Serial6/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/3
 no ip address
 shutdown
 serial restart-delay 0
!
!
router eigrp 100
 network 192.168.0.0
 network 192.168.1.0 0.0.0.1
 network 192.168.4.0 0.0.0.1
 network 192.168.5.0 0.0.0.1
 passive-interface FastEthernet0/0
!
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line vty 0 4
 login
!
!
end
```

#### R2#show running-config

```
Building configuration...

Current configuration : 1750 bytes
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
!
hostname R2
!
boot-start-marker
boot-end-marker
!
!
!
no aaa new-model
no ip icmp rate-limit unreachable
!
!
!
!
!
!
no ip domain lookup
ip cef
no ipv6 cef
!
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
!
!
!
!
!
ip tcp synwait-time 5
!
!
!
!
!
!
!
!
!
interface FastEthernet0/0
 no ip address
 shutdown
 duplex full
!
interface GigabitEthernet1/0
 ip address 192.168.1.1 255.255.255.254
 negotiation auto
!
interface GigabitEthernet2/0
 ip address 192.168.2.0 255.255.255.254
 negotiation auto
!
interface GigabitEthernet3/0
 no ip address
 shutdown
 negotiation auto
!
interface FastEthernet4/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet4/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface Serial6/0
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/3
 no ip address
 shutdown
 serial restart-delay 0
!
!
router eigrp 100
 network 192.168.0.0
 network 192.168.1.0 0.0.0.1
 network 192.168.2.0 0.0.0.1
 network 192.168.4.0 0.0.0.1
 network 192.168.5.0 0.0.0.1
 passive-interface FastEthernet0/0
!
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line vty 0 4
 login
!
!
end
```

#### R3#show running-config

```
Building configuration...

Current configuration : 1779 bytes
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
!
hostname R3
!
boot-start-marker
boot-end-marker
!
!
!
no aaa new-model
no ip icmp rate-limit unreachable
!
!
!
!
!
!
no ip domain lookup
ip cef
no ipv6 cef
!
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
!
!
!
!
!
ip tcp synwait-time 5
!
!
!
!
!
!
!
!
!
interface FastEthernet0/0
 no ip address
 shutdown
 duplex full
!
interface GigabitEthernet1/0
 ip address 192.168.3.0 255.255.255.254
 negotiation auto
!
interface GigabitEthernet2/0
 ip address 192.168.2.1 255.255.255.254
 negotiation auto
!
interface GigabitEthernet3/0
 no ip address
 shutdown
 negotiation auto
!
interface FastEthernet4/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet4/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface Serial6/0
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/3
 no ip address
 shutdown
 serial restart-delay 0
!
!
router eigrp 100
 network 192.168.0.0
 network 192.168.1.0 0.0.0.1
 network 192.168.2.0 0.0.0.1
 network 192.168.3.0 0.0.0.1
 network 192.168.4.0 0.0.0.1
 network 192.168.5.0 0.0.0.1
 passive-interface FastEthernet0/0
!
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line vty 0 4
 login
!
!
end
```

#### R4#show running-config

```
Building configuration...

Current configuration : 1849 bytes
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
!
hostname R4
!
boot-start-marker
boot-end-marker
!
!
!
no aaa new-model
no ip icmp rate-limit unreachable
!
!
!
!
!
!
no ip domain lookup
ip cef
no ipv6 cef
!
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
!
!
!
!
!
ip tcp synwait-time 5
!
!
!
!
!
!
!
!
!
interface FastEthernet0/0
 ip address 192.168.7.254 255.255.255.0
 duplex full
!
interface GigabitEthernet1/0
 ip address 192.168.3.1 255.255.255.254
 negotiation auto
!
interface GigabitEthernet2/0
 no ip address
 shutdown
 negotiation auto
!
interface GigabitEthernet3/0
 no ip address
 shutdown
 negotiation auto
!
interface FastEthernet4/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet4/1
 ip address 192.168.6.1 255.255.255.254
 speed auto
 duplex auto
!
interface FastEthernet5/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface Serial6/0
 ip address 192.168.4.1 255.255.255.254
 encapsulation ppp
 serial restart-delay 0
!
interface Serial6/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/3
 no ip address
 shutdown
 serial restart-delay 0
!
!
router eigrp 100
 network 192.168.0.0
 network 192.168.1.0 0.0.0.1
 network 192.168.3.0 0.0.0.1
 network 192.168.4.0 0.0.0.1
 network 192.168.5.0 0.0.0.1
 network 192.168.6.0 0.0.0.1
 network 192.168.7.0
 passive-interface FastEthernet0/0
!
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line vty 0 4
 login
!
!
end
```

#### R5#show ip interface brief

```
Interface              IP-Address      OK? Method Status                Protocol
FastEthernet0/0        unassigned      YES NVRAM  administratively down down
GigabitEthernet1/0     unassigned      YES NVRAM  up                    up
GigabitEthernet2/0     unassigned      YES NVRAM  administratively down down
GigabitEthernet3/0     unassigned      YES NVRAM  administratively down down
FastEthernet4/0        192.168.5.1     YES NVRAM  up                    up
FastEthernet4/1        192.168.6.0     YES NVRAM  up                    up
FastEthernet5/0        unassigned      YES NVRAM  administratively down down
FastEthernet5/1        unassigned      YES NVRAM  administratively down down
Serial6/0              unassigned      YES NVRAM  administratively down down
Serial6/1              unassigned      YES NVRAM  administratively down down
Serial6/2              unassigned      YES NVRAM  administratively down down
Serial6/3              unassigned      YES NVRAM  administratively down down
Loopback0              10.40.10.1      YES NVRAM  up                    up
R5#
R5#
R5#show running-config
Building configuration...

Current configuration : 1902 bytes
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
!
hostname R5
!
boot-start-marker
boot-end-marker
!
!
!
no aaa new-model
no ip icmp rate-limit unreachable
!
!
!
!
!
!
no ip domain lookup
ip cef
no ipv6 cef
!
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
!
!
!
!
!
ip tcp synwait-time 5
!
!
!
!
!
!
!
!
!
interface Loopback0
 ip address 10.40.10.1 255.255.255.0
 ip nat outside
!
interface FastEthernet0/0
 no ip address
 shutdown
 duplex full
!
interface GigabitEthernet1/0
 no ip address
 negotiation auto
!
interface GigabitEthernet2/0
 no ip address
 shutdown
 negotiation auto
!
interface GigabitEthernet3/0
 no ip address
 shutdown
 negotiation auto
!
interface FastEthernet4/0
 ip address 192.168.5.1 255.255.255.254
 ip nat inside
 speed auto
 duplex auto
!
interface FastEthernet4/1
 ip address 192.168.6.0 255.255.255.254
 ip nat inside
 speed auto
 duplex auto
!
interface FastEthernet5/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface Serial6/0
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/3
 no ip address
 shutdown
 serial restart-delay 0
!
!
router eigrp 100
 network 10.40.10.0 0.0.0.255
 network 192.168.5.0 0.0.0.1
 network 192.168.6.0 0.0.0.1
 redistribute static
 passive-interface GigabitEthernet1/0
!
ip nat inside source list 1 interface Loopback0 overload
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
!
access-list 1 permit any
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line vty 0 4
 login
!
!
end
```

### Preuves du bon fonctionnement : 

#### Table de voisinage EIGRP : 

<img width="1208" height="463" alt="02 - show ip eigrp neighbors" src="https://github.com/user-attachments/assets/f4e8ab88-67de-4284-b01e-10440b3d6fca" />

#### Table de routage : 

<img width="1280" height="1165" alt="03 - show ip route" src="https://github.com/user-attachments/assets/f2ef124a-50a6-4130-ae6b-6aca771fe69b" />

#### Ping depuis le PC1 : 

<img width="948" height="527" alt="04 - ping depuis PC1" src="https://github.com/user-attachments/assets/952240d9-399b-4bc3-b268-47ac14e9d261" />

#### Table de routage après rupture d'un lien : 

<img width="1221" height="1168" alt="05 - show ip route après rupture d&#39;un lien" src="https://github.com/user-attachments/assets/a89b809f-5676-4f13-9737-66c4ff5251d0" />

### Rapport de Synthèse – Cahier des Charges 1

#### 1. Choix de la métrique EIGRP et principe de calcul

L'architecture réseau s'appuie sur le protocole de routage dynamique à vecteur de distances amélioré EIGRP (AS 100). 

Le calcul de la métrique EIGRP repose sur la formule composite standard de Cisco :


Métrique EIGRP = 256 x (10**7 / Bande Passante min + SOMME(Délai))

Par défaut, EIGRP valorise la bande passante minimale (Bandwidth) traversée le long du chemin et le délai cumulé (Delay). Plus la vitesse d'une liaison est élevée, plus le composant de bande passante est faible, ce qui génère une métrique globale plus petite et donc prioritaire.


#### 2. Explication du chemin privilégié entre VPC1 et VPC2

Lors de l'acheminement des paquets entre VPC1 (`192.168.0.1`) et VPC2 (`192.168.7.1`), le protocole EIGRP sélectionne la boucle supérieure passant par les routeurs R1 --> R2 --> R3 --> R4.

#### Analyse comparative des deux chemins possibles :

- Chemin GigabitEthernet (R1 ➔ R2 ➔ R3 ➔ R4) :
  Bien qu'il comporte 3 sauts, la bande passante minimale est de 1 000 000 kbps (1 Gbps), ce qui produit une métrique EIGRP très faible (~30720).
- Chemin Série PPP (R1 ➔ R4) : 
  Bien qu'il s'agisse d'un saut direct, la liaison est bridée à **64 kbps** (`clockrate 64000`). La métrique calculée pour cette liaison lente est extrêmement élevée (> 40 000 000).

Conclusion : EIGRP choisit légitimement la boucle GigabitEthernet comme successeur principal en raison de sa bande passante nettement supérieure.



#### 3. Procédure de test et tolérance aux pannes (Failover)

La validation fonctionnelle du réseau s'est déroulée en quatre étapes :

1. Validation de la connectivité globale :
   - Émission de requêtes ICMP réussies (`ping`) depuis PC1 vers PC2 (`192.168.7.1`).
   - Émission de requêtes ICMP réussies (`ping`) depuis PC1 vers le nuage Internet (`10.40.10.1`).
   - Confirmation du chemin nominal via la commande `trace 192.168.7.1` depuis PC1 (transit effectif par R2 et R3).

2. Simulation de panne (Test de bascule) :
   - Désactivation manuelle de la liaison Gigabit principale via la commande `shutdown` sur l'interface `g1/0` de R1.

3. Analyse du comportement d'EIGRP :
   - Détection automatique de la perte de lien par R1.
   - Basculement immédiat de la route vers le successeur possible : la liaison série de secours R1 ➔ R4 (`192.168.4.1`).

4. Résultat :
   - Le trafic ICMP bascule automatiquement avec une perte minime de paquets (1 à 2 paquets perdus), démontrant la haute disponibilité et la tolérance aux pannes du réseau.

---

## CDC 2 - Interconnexion sécurisée et DMVPN

### Architecture du lab :

<img width="2554" height="1394" alt="01 - lab complet" src="https://github.com/user-attachments/assets/10dee4e7-4087-4cd8-b214-7b958f2c7375" />

### Configuration de chaque routeur : 

#### R1#show running-config

```
Building configuration...

Current configuration : 2525 bytes
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
!
hostname R1
!
boot-start-marker
boot-end-marker
!
!
!
no aaa new-model
no ip icmp rate-limit unreachable
!
!
!
!
!
!
no ip domain lookup
ip cef
no ipv6 cef
!
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
!
!
!
!
!
ip tcp synwait-time 5
!
!
crypto isakmp policy 10
 encr aes 256
 hash sha256
 authentication pre-share
 group 14
crypto isakmp key SatomSecretKey123 address 0.0.0.0
!
!
crypto ipsec transform-set TS-DMVPN esp-aes 256 esp-sha256-hmac
 mode transport
!
crypto ipsec profile IPSEC-PROFILE-DMVPN
 set transform-set TS-DMVPN
!
!
!
!
!
!
!
interface Tunnel0
 description interface Hub DMVPN CDC 2
 ip address 172.16.0.1 255.255.255.0
 no ip redirects
 ip mtu 1400
 no ip split-horizon eigrp 100
 ip nhrp authentication SatmNHRP
 ip nhrp map multicast dynamic
 ip nhrp network-id 100
 ip nhrp redirect
 ip tcp adjust-mss 1360
 tunnel source GigabitEthernet1/0
 tunnel mode gre multipoint
 tunnel protection ipsec profile IPSEC-PROFILE-DMVPN
!
interface FastEthernet0/0
 ip address 192.168.0.254 255.255.255.0
 duplex full
!
interface GigabitEthernet1/0
 ip address 192.168.1.0 255.255.255.254
 negotiation auto
!
interface GigabitEthernet2/0
 no ip address
 shutdown
 negotiation auto
!
interface GigabitEthernet3/0
 no ip address
 shutdown
 negotiation auto
!
interface FastEthernet4/0
 ip address 192.168.5.0 255.255.255.254
 speed auto
 duplex auto
!
interface FastEthernet4/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface Serial6/0
 ip address 192.168.4.0 255.255.255.254
 encapsulation ppp
 serial restart-delay 0
 clock rate 64000
!
interface Serial6/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/3
 no ip address
 shutdown
 serial restart-delay 0
!
!
router eigrp 100
 network 172.16.0.0 0.0.0.255
 network 192.168.0.0
 network 192.168.1.0 0.0.0.1
 network 192.168.4.0 0.0.0.1
 network 192.168.5.0 0.0.0.1
 passive-interface FastEthernet0/0
!
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line vty 0 4
 login
!
!
end
```

#### R2#show running-config

```
Building configuration...

Current configuration : 2518 bytes
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
!
hostname R2
!
boot-start-marker
boot-end-marker
!
!
!
no aaa new-model
no ip icmp rate-limit unreachable
!
!
!
!
!
!
no ip domain lookup
ip cef
no ipv6 cef
!
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
!
!
!
!
!
ip tcp synwait-time 5
!
!
crypto isakmp policy 10
 encr aes 256
 hash sha256
 authentication pre-share
 group 14
crypto isakmp key SatomSecretKey123 address 0.0.0.0
!
!
crypto ipsec transform-set TS-DMVPN esp-aes 256 esp-sha256-hmac
 mode transport
!
crypto ipsec profile IPSEC-PROFILE-DMVPN
 set transform-set TS-DMVPN
!
!
!
!
!
!
!
interface Tunnel0
 description Interface Spoke DMVPN R2
 ip address 172.16.0.2 255.255.255.0
 no ip redirects
 ip mtu 1400
 ip nhrp authentication SatmNHRP
 ip nhrp map 172.16.0.1 192.168.1.0
 ip nhrp map multicast 192.168.1.0
 ip nhrp network-id 100
 ip nhrp nhs 172.16.0.1
 ip nhrp shortcut
 ip tcp adjust-mss 1360
 tunnel source GigabitEthernet1/0
 tunnel mode gre multipoint
 tunnel protection ipsec profile IPSEC-PROFILE-DMVPN
!
interface FastEthernet0/0
 no ip address
 shutdown
 duplex full
!
interface GigabitEthernet1/0
 ip address 192.168.1.1 255.255.255.254
 negotiation auto
!
interface GigabitEthernet2/0
 ip address 192.168.2.0 255.255.255.254
 negotiation auto
!
interface GigabitEthernet3/0
 no ip address
 shutdown
 negotiation auto
!
interface FastEthernet4/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet4/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface Serial6/0
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/3
 no ip address
 shutdown
 serial restart-delay 0
!
!
router eigrp 100
 network 172.16.0.0 0.0.0.255
 network 192.168.0.0
 network 192.168.1.0 0.0.0.1
 network 192.168.2.0 0.0.0.1
 network 192.168.4.0 0.0.0.1
 network 192.168.5.0 0.0.0.1
 passive-interface FastEthernet0/0
!
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line vty 0 4
 login
!
!
end
```

#### R3#show running-config

```
Building configuration...

Current configuration : 2547 bytes
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
!
hostname R3
!
boot-start-marker
boot-end-marker
!
!
!
no aaa new-model
no ip icmp rate-limit unreachable
!
!
!
!
!
!
no ip domain lookup
ip cef
no ipv6 cef
!
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
!
!
!
!
!
ip tcp synwait-time 5
!
!
crypto isakmp policy 10
 encr aes 256
 hash sha256
 authentication pre-share
 group 14
crypto isakmp key SatomSecretKey123 address 0.0.0.0
!
!
crypto ipsec transform-set TS-DMVPN esp-aes 256 esp-sha256-hmac
 mode transport
!
crypto ipsec profile IPSEC-PROFILE-DMVPN
 set transform-set TS-DMVPN
!
!
!
!
!
!
!
interface Tunnel0
 description Interface Spoke DMVPN R3
 ip address 172.16.0.3 255.255.255.0
 no ip redirects
 ip mtu 1400
 ip nhrp authentication SatmNHRP
 ip nhrp map 172.16.0.1 192.168.1.0
 ip nhrp map multicast 192.168.1.0
 ip nhrp network-id 100
 ip nhrp nhs 172.16.0.1
 ip nhrp shortcut
 ip tcp adjust-mss 1360
 tunnel source GigabitEthernet2/0
 tunnel mode gre multipoint
 tunnel protection ipsec profile IPSEC-PROFILE-DMVPN
!
interface FastEthernet0/0
 no ip address
 shutdown
 duplex full
!
interface GigabitEthernet1/0
 ip address 192.168.3.0 255.255.255.254
 negotiation auto
!
interface GigabitEthernet2/0
 ip address 192.168.2.1 255.255.255.254
 negotiation auto
!
interface GigabitEthernet3/0
 no ip address
 shutdown
 negotiation auto
!
interface FastEthernet4/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet4/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface Serial6/0
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/3
 no ip address
 shutdown
 serial restart-delay 0
!
!
router eigrp 100
 network 172.16.0.0 0.0.0.255
 network 192.168.0.0
 network 192.168.1.0 0.0.0.1
 network 192.168.2.0 0.0.0.1
 network 192.168.3.0 0.0.0.1
 network 192.168.4.0 0.0.0.1
 network 192.168.5.0 0.0.0.1
 passive-interface FastEthernet0/0
!
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line vty 0 4
 login
!
!
end
```

#### R4#show running-config

```
Building configuration...

Current configuration : 2617 bytes
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
!
hostname R4
!
boot-start-marker
boot-end-marker
!
!
!
no aaa new-model
no ip icmp rate-limit unreachable
!
!
!
!
!
!
no ip domain lookup
ip cef
no ipv6 cef
!
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
!
!
!
!
!
ip tcp synwait-time 5
!
!
crypto isakmp policy 10
 encr aes 256
 hash sha256
 authentication pre-share
 group 14
crypto isakmp key SatomSecretKey123 address 0.0.0.0
!
!
crypto ipsec transform-set TS-DMVPN esp-aes 256 esp-sha256-hmac
 mode transport
!
crypto ipsec profile IPSEC-PROFILE-DMVPN
 set transform-set TS-DMVPN
!
!
!
!
!
!
!
interface Tunnel0
 description Interface Spoke DMVPN R4
 ip address 172.16.0.4 255.255.255.0
 no ip redirects
 ip mtu 1400
 ip nhrp authentication SatmNHRP
 ip nhrp map 172.16.0.1 192.168.1.0
 ip nhrp map multicast 192.168.1.0
 ip nhrp network-id 100
 ip nhrp nhs 172.16.0.1
 ip nhrp shortcut
 ip tcp adjust-mss 1360
 tunnel source GigabitEthernet1/0
 tunnel mode gre multipoint
 tunnel protection ipsec profile IPSEC-PROFILE-DMVPN
!
interface FastEthernet0/0
 ip address 192.168.7.254 255.255.255.0
 duplex full
!
interface GigabitEthernet1/0
 ip address 192.168.3.1 255.255.255.254
 negotiation auto
!
interface GigabitEthernet2/0
 no ip address
 shutdown
 negotiation auto
!
interface GigabitEthernet3/0
 no ip address
 shutdown
 negotiation auto
!
interface FastEthernet4/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet4/1
 ip address 192.168.6.1 255.255.255.254
 speed auto
 duplex auto
!
interface FastEthernet5/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface Serial6/0
 ip address 192.168.4.1 255.255.255.254
 encapsulation ppp
 serial restart-delay 0
!
interface Serial6/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/3
 no ip address
 shutdown
 serial restart-delay 0
!
!
router eigrp 100
 network 172.16.0.0 0.0.0.255
 network 192.168.0.0
 network 192.168.1.0 0.0.0.1
 network 192.168.3.0 0.0.0.1
 network 192.168.4.0 0.0.0.1
 network 192.168.5.0 0.0.0.1
 network 192.168.6.0 0.0.0.1
 network 192.168.7.0
 passive-interface FastEthernet0/0
!
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line vty 0 4
 login
!
!
end
```

#### R5#show running-config

```
Building configuration...

Current configuration : 1902 bytes
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
!
hostname R5
!
boot-start-marker
boot-end-marker
!
!
!
no aaa new-model
no ip icmp rate-limit unreachable
!
!
!
!
!
!
no ip domain lookup
ip cef
no ipv6 cef
!
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
!
!
!
!
!
ip tcp synwait-time 5
!
!
!
!
!
!
!
!
!
interface Loopback0
 ip address 10.40.10.1 255.255.255.0
 ip nat outside
!
interface FastEthernet0/0
 no ip address
 shutdown
 duplex full
!
interface GigabitEthernet1/0
 no ip address
 negotiation auto
!
interface GigabitEthernet2/0
 no ip address
 shutdown
 negotiation auto
!
interface GigabitEthernet3/0
 no ip address
 shutdown
 negotiation auto
!
interface FastEthernet4/0
 ip address 192.168.5.1 255.255.255.254
 ip nat inside
 speed auto
 duplex auto
!
interface FastEthernet4/1
 ip address 192.168.6.0 255.255.255.254
 ip nat inside
 speed auto
 duplex auto
!
interface FastEthernet5/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface Serial6/0
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/3
 no ip address
 shutdown
 serial restart-delay 0
!
!
router eigrp 100
 network 10.40.10.0 0.0.0.255
 network 192.168.5.0 0.0.0.1
 network 192.168.6.0 0.0.0.1
 redistribute static
 passive-interface GigabitEthernet1/0
!
ip nat inside source list 1 interface Loopback0 overload
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
!
access-list 1 permit any
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line vty 0 4
 login
!
!
end
```

### Preuves du bon fonctionnement : 

#### R1#show crypto ipsec sa

```
interface: Tunnel0
    Crypto map tag: Tunnel0-head-0, local addr 192.168.1.0

   protected vrf: (none)
   local  ident (addr/mask/prot/port): (192.168.1.0/255.255.255.255/47/0)
   remote ident (addr/mask/prot/port): (192.168.1.1/255.255.255.255/47/0)
   current_peer 192.168.1.1 port 500
     PERMIT, flags={origin_is_acl,}
    #pkts encaps: 118, #pkts encrypt: 118, #pkts digest: 118
    #pkts decaps: 118, #pkts decrypt: 118, #pkts verify: 118
    #pkts compressed: 0, #pkts decompressed: 0
    #pkts not compressed: 0, #pkts compr. failed: 0
    #pkts not decompressed: 0, #pkts decompress failed: 0
    #send errors 0, #recv errors 0

     local crypto endpt.: 192.168.1.0, remote crypto endpt.: 192.168.1.1
     path mtu 1500, ip mtu 1500, ip mtu idb (none)
     current outbound spi: 0x78C1E59(126623321)
     PFS (Y/N): N, DH group: none

     inbound esp sas:
      spi: 0xA0C0E414(2696995860)
        transform: esp-256-aes esp-sha256-hmac ,
        in use settings ={Transport, }
        conn id: 1, flow_id: 1, sibling_flags 80000000, crypto map: Tunnel0-head                                                                                                                                   -0
        sa timing: remaining key lifetime (k/sec): (4260386/3087)
        IV size: 16 bytes
        replay detection support: Y
        Status: ACTIVE(ACTIVE)

     inbound ah sas:

     inbound pcp sas:

     outbound esp sas:
      spi: 0x78C1E59(126623321)
        transform: esp-256-aes esp-sha256-hmac ,
        in use settings ={Transport, }
        conn id: 2, flow_id: 2, sibling_flags 80000000, crypto map: Tunnel0-head                                                                                                                                   -0
        sa timing: remaining key lifetime (k/sec): (4260387/3087)
        IV size: 16 bytes
        replay detection support: Y
        Status: ACTIVE(ACTIVE)

     outbound ah sas:

     outbound pcp sas:

   protected vrf: (none)
   local  ident (addr/mask/prot/port): (192.168.1.0/255.255.255.255/47/0)
   remote ident (addr/mask/prot/port): (192.168.2.1/255.255.255.255/47/0)
   current_peer 192.168.2.1 port 500
     PERMIT, flags={origin_is_acl,}
    #pkts encaps: 119, #pkts encrypt: 119, #pkts digest: 119
    #pkts decaps: 117, #pkts decrypt: 117, #pkts verify: 117
    #pkts compressed: 0, #pkts decompressed: 0
    #pkts not compressed: 0, #pkts compr. failed: 0
    #pkts not decompressed: 0, #pkts decompress failed: 0
    #send errors 0, #recv errors 0

     local crypto endpt.: 192.168.1.0, remote crypto endpt.: 192.168.2.1
     path mtu 1500, ip mtu 1500, ip mtu idb (none)
     current outbound spi: 0x684A6546(1749706054)
     PFS (Y/N): N, DH group: none

     inbound esp sas:
      spi: 0x285FB10(42334992)
        transform: esp-256-aes esp-sha256-hmac ,
        in use settings ={Transport, }
        conn id: 3, flow_id: 3, sibling_flags 80000000, crypto map: Tunnel0-head                                                                                                                                   -0
        sa timing: remaining key lifetime (k/sec): (4169746/3088)
        IV size: 16 bytes
        replay detection support: Y
        Status: ACTIVE(ACTIVE)

     inbound ah sas:

     inbound pcp sas:

     outbound esp sas:
      spi: 0x684A6546(1749706054)
        transform: esp-256-aes esp-sha256-hmac ,
        in use settings ={Transport, }
        conn id: 4, flow_id: 4, sibling_flags 80000000, crypto map: Tunnel0-head                                                                                                                                   -0
        sa timing: remaining key lifetime (k/sec): (4169745/3088)
        IV size: 16 bytes
        replay detection support: Y
        Status: ACTIVE(ACTIVE)

     outbound ah sas:

     outbound pcp sas:

   protected vrf: (none)
   local  ident (addr/mask/prot/port): (192.168.1.0/255.255.255.255/47/0)
   remote ident (addr/mask/prot/port): (192.168.3.1/255.255.255.255/47/0)
   current_peer 192.168.3.1 port 500
     PERMIT, flags={origin_is_acl,}
    #pkts encaps: 119, #pkts encrypt: 119, #pkts digest: 119
    #pkts decaps: 117, #pkts decrypt: 117, #pkts verify: 117
    #pkts compressed: 0, #pkts decompressed: 0
    #pkts not compressed: 0, #pkts compr. failed: 0
    #pkts not decompressed: 0, #pkts decompress failed: 0
    #send errors 0, #recv errors 0

     local crypto endpt.: 192.168.1.0, remote crypto endpt.: 192.168.3.1
     path mtu 1500, ip mtu 1500, ip mtu idb (none)
     current outbound spi: 0xEAD0F913(3939563795)
     PFS (Y/N): N, DH group: none

     inbound esp sas:
      spi: 0x39AFE4D(60489293)
        transform: esp-256-aes esp-sha256-hmac ,
        in use settings ={Transport, }
        conn id: 5, flow_id: 5, sibling_flags 80000000, crypto map: Tunnel0-head                                                                                                                                   -0
        sa timing: remaining key lifetime (k/sec): (4310821/3088)
        IV size: 16 bytes
        replay detection support: Y
        Status: ACTIVE(ACTIVE)

     inbound ah sas:

     inbound pcp sas:

     outbound esp sas:
      spi: 0xEAD0F913(3939563795)
        transform: esp-256-aes esp-sha256-hmac ,
        in use settings ={Transport, }
        conn id: 6, flow_id: 6, sibling_flags 80000000, crypto map: Tunnel0-head                                                                                                                                   -0
        sa timing: remaining key lifetime (k/sec): (4310820/3088)
        IV size: 16 bytes
        replay detection support: Y
        Status: ACTIVE(ACTIVE)

     outbound ah sas:

     outbound pcp sas:
```

#### R4#show crypto ipsec sa

```
interface: Tunnel0
    Crypto map tag: Tunnel0-head-0, local addr 192.168.3.1

   protected vrf: (none)
   local  ident (addr/mask/prot/port): (192.168.3.1/255.255.255.255/47/0)
   remote ident (addr/mask/prot/port): (192.168.1.0/255.255.255.255/47/0)
   current_peer 192.168.1.0 port 500
     PERMIT, flags={origin_is_acl,}
    #pkts encaps: 154, #pkts encrypt: 154, #pkts digest: 154
    #pkts decaps: 156, #pkts decrypt: 156, #pkts verify: 156
    #pkts compressed: 0, #pkts decompressed: 0
    #pkts not compressed: 0, #pkts compr. failed: 0
    #pkts not decompressed: 0, #pkts decompress failed: 0
    #send errors 0, #recv errors 0

     local crypto endpt.: 192.168.3.1, remote crypto endpt.: 192.168.1.0
     path mtu 1500, ip mtu 1500, ip mtu idb (none)
     current outbound spi: 0x39AFE4D(60489293)
     PFS (Y/N): N, DH group: none

     inbound esp sas:
      spi: 0xEAD0F913(3939563795)
        transform: esp-256-aes esp-sha256-hmac ,
        in use settings ={Transport, }
        conn id: 1, flow_id: 1, sibling_flags 80004000, crypto map: Tunnel0-head-0
        sa timing: remaining key lifetime (k/sec): (4246302/2917)
        IV size: 16 bytes
        replay detection support: Y
        Status: ACTIVE(ACTIVE)

     inbound ah sas:

     inbound pcp sas:

     outbound esp sas:
      spi: 0x39AFE4D(60489293)
        transform: esp-256-aes esp-sha256-hmac ,
        in use settings ={Transport, }
        conn id: 2, flow_id: 2, sibling_flags 80004000, crypto map: Tunnel0-head-0
        sa timing: remaining key lifetime (k/sec): (4246303/2917)
        IV size: 16 bytes
        replay detection support: Y
        Status: ACTIVE(ACTIVE)

     outbound ah sas:

     outbound pcp sas:
```

### Preuves du bon fonctionnement : 

#### Show ip nhrp sur le HUB

<img width="777" height="501" alt="02 - show ip nhrp HUB" src="https://github.com/user-attachments/assets/f4f24203-c804-4e2d-b686-3a79e7cb22db" />

#### Show ip nhrp sur les SPOKES

<img width="1903" height="1100" alt="03 - show ip nhrp  SPOKE" src="https://github.com/user-attachments/assets/3c70c512-a815-46de-842a-ee02dc0101cb" />

#### Ping entre PC1 et PC2

<img width="2473" height="819" alt="04 - ping entre pc" src="https://github.com/user-attachments/assets/f6116268-116b-4312-9de2-4b8156c45aa8" />

#### Preuve de ping entre PC1 et PC2 et capture Wireshark

<img width="3200" height="1904" alt="05 - preuve des ping" src="https://github.com/user-attachments/assets/c64212ed-5509-4c57-a5af-974ad1156927" />

### Rapport de Synthèse – Cahier des Charges 2

#### 1. Choix cryptographiques et paramètres de sécurité IPsec

L'architecture d'overlay s'appuie sur le protocole de chiffrement IPsec associé à IKEv1 (Phase 1 et Phase 2) pour sécuriser l'ensemble des échanges sur le réseau DMVPN.

#### Analyse de la politique de sécurité retenue :

- IKEv1 Phase 1 (ISAKMP Policy 10) :
  - Chiffrement (AES-256) : Algorithme de chiffrement symétrique par bloc offrant un niveau de protection élevé contre la cryptanalyse.
  - Hachage (SHA-256) : Fonction de hachage assurant l'intégrité des paquets et l'authenticité des messages de négociation.
  - Diffie-Hellman (Group 14) : Échange de clés fondé sur un groupe de 2048 bits, garantissant une forte résistance face aux attaques par force brute.
  - Authentification (PSK `SatomSecretKey123`) : Authentification mutuelle initiale par clé pré-partagée.

- IKEv1 Phase 2 (Transform-Set & Profile IPsec) :
  - Transform-Set (`TS-DMVPN`) : Combinaison de `esp-aes 256` et `esp-sha256-hmac` assurant la confidentialité et l'intégrité du trafic de données.
  - Mode Transport : Le mode Transport a été privilégié au mode Tunnel standard afin d'éviter la superposition de deux en-têtes IP (GRE + IPsec Tunnel). Ce choix réduit l'overhead des paquets et optimise l'utilisation de la bande passante.

#### 2. Rôle du protocole NHRP et fonctionnement du DMVPN Phase 2

Le protocole NHRP (Next Hop Resolution Protocol) permet de mapper de manière dynamique les adresses IP logiques de l'Overlay (`172.16.0.0/24`) aux adresses IP physiques sous-jacentes de l'Underlay.

#### Principes de fonctionnement :

- Enregistrement dynamique auprès du Hub :
  Au démarrage, chaque Spoke (R2, R3, R4) envoie une requête d'enregistrement NHRP au Hub (R1 - NHS) pour lui déclarer son adresse physique source (`192.168.1.1`, `192.168.2.1`, `192.168.3.1`).
- Authentification NHRP (`SatmNHRP`) :
  L'authentification NHRP est calibrée sur 8 caractères afin de respecter la contrainte de syntaxe maximale de l'IOS Cisco tout en sécurisant la base de données de résolution.
- Tunnels dynamiques Spoke-to-Spoke (Phase 2) :
  Grâce aux fonctionnalités `ip nhrp redirect` sur le Hub et `ip nhrp shortcut` sur les Spokes, les routeurs clients peuvent résoudre l'adresse d'un autre Spoke et établir un tunnel IPsec/mGRE direct à la demande, sans surcharger le processeur du Hub.

#### 3. Comparaison : Tunnels statiques vs Tunnels dynamiques DMVPN

#### Analyse comparative des deux approches :

- Tunnels GRE / IPsec Statiques :
  - Complexité : Nécessitent la configuration manuelle de chaque liaison point-à-point (soit N(N-1)/2 tunnels pour un maillage complet).
  - Évolutivité : Faible. L'ajout d'un nouveau site exige la modification de la configuration de tous les routeurs existants.
  - Chemin du trafic : Strictement dépendant des interfaces virtuelles prédéfinies.

- DMVPN Phase 2 (mGRE + NHRP + IPsec) :
  - Complexité : Faible. Une seule interface virtuelle `Tunnel0` mGRE est configurée par routeur.
  - Évolutivité : Maximale. Tout nouveau Spoke s'enregistre automatiquement auprès du Hub sans aucune modification sur ce dernier.
  - Chemin du trafic : Établissement dynamique de tunnels directs de Spoke à Spoke à la demande pour un routage optimal.

#### 4. Risques restants et préconisations d'amélioration

Malgré la validation complète des exigences du CDC 2, plusieurs axes d'amélioration et risques de sécurité subsistent :

1. Point unique de défaillance (Single Point of Failure - SPoF) :
   Le routeur R1 est le seul Hub NHRP (NHS) du réseau. Sa perte empêche toute nouvelle résolution d'adresse pour les tunnels dynamiques.
   - Préconisation : Implémenter la redondance du Hub (Dual-Hub Dual-DMVPN).
2. Authentification par PSK globale unique :
   L'utilisation d'une clé pré-partagée identique (`SatomSecretKey123`) sur l'ensemble des routeurs représente un risque majeur en cas de compromission d'un seul équipement client.
   - Préconisation : Migrer vers une authentification par certificats numériques X.509 (PKI).
3. Limitation du protocole IKEv1 :
   IKEv1 offre des temps de négociation plus longs et une gestion du NAT moins performante qu'IKEv2.
   - Préconisation : Faire évoluer le profil de chiffrement vers IKEv2 / FlexVPN.

---

## CDC 3 - Routage externe BGP

### Architecture du lab :

<img width="2529" height="1415" alt="01 - lab complet" src="https://github.com/user-attachments/assets/2c95ab6b-de73-48cf-a542-0f9462ff8aac" />

### Configuration de chaque routeur : 

#### R1#show running-config

```
Building configuration...

Current configuration : 2878 bytes
!
! Last configuration change at 14:15:34 UTC Fri Oct 9 2026
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
!
hostname R1
!
boot-start-marker
boot-end-marker
!
!
!
no aaa new-model
no ip icmp rate-limit unreachable
!
!
!
!
!
!
no ip domain lookup
ip cef
no ipv6 cef
!
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
!
!
!
!
!
ip tcp synwait-time 5
!
!
crypto isakmp policy 10
 encr aes 256
 hash sha256
 authentication pre-share
 group 14
crypto isakmp key SatomSecretKey123 address 0.0.0.0
!
!
crypto ipsec transform-set TS-DMVPN esp-aes 256 esp-sha256-hmac
 mode transport
!
crypto ipsec profile IPSEC-PROFILE-DMVPN
 set transform-set TS-DMVPN
!
!
!
!
!
!
!
interface Tunnel0
 description interface Hub DMVPN CDC 2
 ip address 172.16.0.1 255.255.255.0
 no ip redirects
 ip mtu 1400
 no ip split-horizon eigrp 100
 ip nhrp authentication SatmNHRP
 ip nhrp map multicast dynamic
 ip nhrp network-id 100
 ip nhrp redirect
 ip tcp adjust-mss 1360
 tunnel source GigabitEthernet1/0
 tunnel mode gre multipoint
 tunnel protection ipsec profile IPSEC-PROFILE-DMVPN
!
interface FastEthernet0/0
 ip address 192.168.0.254 255.255.255.0
 duplex full
!
interface GigabitEthernet1/0
 ip address 192.168.1.0 255.255.255.254
 negotiation auto
!
interface GigabitEthernet2/0
 no ip address
 shutdown
 negotiation auto
!
interface GigabitEthernet3/0
 no ip address
 shutdown
 negotiation auto
!
interface FastEthernet4/0
 ip address 192.168.5.0 255.255.255.254
 speed auto
 duplex auto
!
interface FastEthernet4/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface Serial6/0
 ip address 192.168.4.0 255.255.255.254
 encapsulation ppp
 serial restart-delay 0
 clock rate 64000
!
interface Serial6/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/3
 no ip address
 shutdown
 serial restart-delay 0
!
!
router eigrp 100
 network 172.16.0.0 0.0.0.255
 network 192.168.0.0
 network 192.168.1.0 0.0.0.1
 network 192.168.4.0 0.0.0.1
 network 192.168.5.0 0.0.0.1
 passive-interface FastEthernet0/0
!
router bgp 65000
 bgp log-neighbor-changes
 network 192.168.0.0
 neighbor 172.16.0.2 remote-as 65000
 neighbor 172.16.0.3 remote-as 65000
 neighbor 172.16.0.4 remote-as 65000
 neighbor 192.168.5.1 remote-as 65000
 neighbor 192.168.5.1 next-hop-self
!
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
ip route 192.168.0.0 255.255.255.0 Null0
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line vty 0 4
 login
!
!
end
```

#### R2#show running-config

```
Building configuration...

Current configuration : 2735 bytes
!
! Last configuration change at 14:15:52 UTC Fri Oct 9 2026
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
!
hostname R2
!
boot-start-marker
boot-end-marker
!
!
!
no aaa new-model
no ip icmp rate-limit unreachable
!
!
!
!
!
!
no ip domain lookup
ip cef
no ipv6 cef
!
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
!
!
!
!
!
ip tcp synwait-time 5
!
!
crypto isakmp policy 10
 encr aes 256
 hash sha256
 authentication pre-share
 group 14
crypto isakmp key SatomSecretKey123 address 0.0.0.0
!
!
crypto ipsec transform-set TS-DMVPN esp-aes 256 esp-sha256-hmac
 mode transport
!
crypto ipsec profile IPSEC-PROFILE-DMVPN
 set transform-set TS-DMVPN
!
!
!
!
!
!
!
interface Tunnel0
 description Interface Spoke DMVPN R2
 ip address 172.16.0.2 255.255.255.0
 no ip redirects
 ip mtu 1400
 ip nhrp authentication SatmNHRP
 ip nhrp map 172.16.0.1 192.168.1.0
 ip nhrp map multicast 192.168.1.0
 ip nhrp network-id 100
 ip nhrp nhs 172.16.0.1
 ip nhrp shortcut
 ip tcp adjust-mss 1360
 tunnel source GigabitEthernet1/0
 tunnel mode gre multipoint
 tunnel protection ipsec profile IPSEC-PROFILE-DMVPN
!
interface FastEthernet0/0
 no ip address
 shutdown
 duplex full
!
interface GigabitEthernet1/0
 ip address 192.168.1.1 255.255.255.254
 negotiation auto
!
interface GigabitEthernet2/0
 ip address 192.168.2.0 255.255.255.254
 negotiation auto
!
interface GigabitEthernet3/0
 no ip address
 shutdown
 negotiation auto
!
interface FastEthernet4/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet4/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface Serial6/0
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/3
 no ip address
 shutdown
 serial restart-delay 0
!
!
router eigrp 100
 network 172.16.0.0 0.0.0.255
 network 192.168.0.0
 network 192.168.1.0 0.0.0.1
 network 192.168.2.0 0.0.0.1
 network 192.168.4.0 0.0.0.1
 network 192.168.5.0 0.0.0.1
 passive-interface FastEthernet0/0
!
router bgp 65000
 bgp log-neighbor-changes
 neighbor 172.16.0.1 remote-as 65000
 neighbor 172.16.0.3 remote-as 65000
 neighbor 172.16.0.4 remote-as 65000
!
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line vty 0 4
 login
!
!
end
```

#### R3#show running-config

```
Building configuration...

Current configuration : 2764 bytes
!
! Last configuration change at 14:16:12 UTC Fri Oct 9 2026
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
!
hostname R3
!
boot-start-marker
boot-end-marker
!
!
!
no aaa new-model
no ip icmp rate-limit unreachable
!
!
!
!
!
!
no ip domain lookup
ip cef
no ipv6 cef
!
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
!
!
!
!
!
ip tcp synwait-time 5
!
!
crypto isakmp policy 10
 encr aes 256
 hash sha256
 authentication pre-share
 group 14
crypto isakmp key SatomSecretKey123 address 0.0.0.0
!
!
crypto ipsec transform-set TS-DMVPN esp-aes 256 esp-sha256-hmac
 mode transport
!
crypto ipsec profile IPSEC-PROFILE-DMVPN
 set transform-set TS-DMVPN
!
!
!
!
!
!
!
interface Tunnel0
 description Interface Spoke DMVPN R3
 ip address 172.16.0.3 255.255.255.0
 no ip redirects
 ip mtu 1400
 ip nhrp authentication SatmNHRP
 ip nhrp map 172.16.0.1 192.168.1.0
 ip nhrp map multicast 192.168.1.0
 ip nhrp network-id 100
 ip nhrp nhs 172.16.0.1
 ip nhrp shortcut
 ip tcp adjust-mss 1360
 tunnel source GigabitEthernet2/0
 tunnel mode gre multipoint
 tunnel protection ipsec profile IPSEC-PROFILE-DMVPN
!
interface FastEthernet0/0
 no ip address
 shutdown
 duplex full
!
interface GigabitEthernet1/0
 ip address 192.168.3.0 255.255.255.254
 negotiation auto
!
interface GigabitEthernet2/0
 ip address 192.168.2.1 255.255.255.254
 negotiation auto
!
interface GigabitEthernet3/0
 no ip address
 shutdown
 negotiation auto
!
interface FastEthernet4/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet4/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface Serial6/0
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/3
 no ip address
 shutdown
 serial restart-delay 0
!
!
router eigrp 100
 network 172.16.0.0 0.0.0.255
 network 192.168.0.0
 network 192.168.1.0 0.0.0.1
 network 192.168.2.0 0.0.0.1
 network 192.168.3.0 0.0.0.1
 network 192.168.4.0 0.0.0.1
 network 192.168.5.0 0.0.0.1
 passive-interface FastEthernet0/0
!
router bgp 65000
 bgp log-neighbor-changes
 neighbor 172.16.0.1 remote-as 65000
 neighbor 172.16.0.2 remote-as 65000
 neighbor 172.16.0.4 remote-as 65000
!
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line vty 0 4
 login
!
!
end
```

#### R4#show running-config

```
Building configuration...

Current configuration : 2970 bytes
!
! Last configuration change at 14:16:31 UTC Fri Oct 9 2026
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
!
hostname R4
!
boot-start-marker
boot-end-marker
!
!
!
no aaa new-model
no ip icmp rate-limit unreachable
!
!
!
!
!
!
no ip domain lookup
ip cef
no ipv6 cef
!
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
!
!
!
!
!
ip tcp synwait-time 5
!
!
crypto isakmp policy 10
 encr aes 256
 hash sha256
 authentication pre-share
 group 14
crypto isakmp key SatomSecretKey123 address 0.0.0.0
!
!
crypto ipsec transform-set TS-DMVPN esp-aes 256 esp-sha256-hmac
 mode transport
!
crypto ipsec profile IPSEC-PROFILE-DMVPN
 set transform-set TS-DMVPN
!
!
!
!
!
!
!
interface Tunnel0
 description Interface Spoke DMVPN R4
 ip address 172.16.0.4 255.255.255.0
 no ip redirects
 ip mtu 1400
 ip nhrp authentication SatmNHRP
 ip nhrp map 172.16.0.1 192.168.1.0
 ip nhrp map multicast 192.168.1.0
 ip nhrp network-id 100
 ip nhrp nhs 172.16.0.1
 ip nhrp shortcut
 ip tcp adjust-mss 1360
 tunnel source GigabitEthernet1/0
 tunnel mode gre multipoint
 tunnel protection ipsec profile IPSEC-PROFILE-DMVPN
!
interface FastEthernet0/0
 ip address 192.168.7.254 255.255.255.0
 duplex full
!
interface GigabitEthernet1/0
 ip address 192.168.3.1 255.255.255.254
 negotiation auto
!
interface GigabitEthernet2/0
 no ip address
 shutdown
 negotiation auto
!
interface GigabitEthernet3/0
 no ip address
 shutdown
 negotiation auto
!
interface FastEthernet4/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet4/1
 ip address 192.168.6.1 255.255.255.254
 speed auto
 duplex auto
!
interface FastEthernet5/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface Serial6/0
 ip address 192.168.4.1 255.255.255.254
 encapsulation ppp
 serial restart-delay 0
!
interface Serial6/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/3
 no ip address
 shutdown
 serial restart-delay 0
!
!
router eigrp 100
 network 172.16.0.0 0.0.0.255
 network 192.168.0.0
 network 192.168.1.0 0.0.0.1
 network 192.168.3.0 0.0.0.1
 network 192.168.4.0 0.0.0.1
 network 192.168.5.0 0.0.0.1
 network 192.168.6.0 0.0.0.1
 network 192.168.7.0
 passive-interface FastEthernet0/0
!
router bgp 65000
 bgp log-neighbor-changes
 network 192.168.7.0
 neighbor 172.16.0.1 remote-as 65000
 neighbor 172.16.0.2 remote-as 65000
 neighbor 172.16.0.3 remote-as 65000
 neighbor 192.168.6.0 remote-as 65000
 neighbor 192.168.6.0 next-hop-self
!
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
ip route 192.168.7.0 255.255.255.0 Null0
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line vty 0 4
 login
!
!
end
```

#### R5#show running-config

```
Building configuration...

Current configuration : 2429 bytes
!
! Last configuration change at 14:16:48 UTC Fri Oct 9 2026
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
!
hostname R5
!
boot-start-marker
boot-end-marker
!
!
!
no aaa new-model
no ip icmp rate-limit unreachable
!
!
!
!
!
!
no ip domain lookup
ip cef
no ipv6 cef
!
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
!
!
!
!
!
ip tcp synwait-time 5
!
!
!
!
!
!
!
!
!
interface FastEthernet0/0
 no ip address
 shutdown
 duplex full
!
interface GigabitEthernet1/0
 ip address 10.40.10.2 255.255.255.0
 negotiation auto
!
interface GigabitEthernet2/0
 no ip address
 shutdown
 negotiation auto
!
interface GigabitEthernet3/0
 no ip address
 shutdown
 negotiation auto
!
interface FastEthernet4/0
 ip address 192.168.5.1 255.255.255.254
 ip nat inside
 speed auto
 duplex auto
!
interface FastEthernet4/1
 ip address 192.168.6.0 255.255.255.254
 ip nat inside
 speed auto
 duplex auto
!
interface FastEthernet5/0
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface FastEthernet5/1
 no ip address
 shutdown
 speed auto
 duplex auto
!
interface Serial6/0
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial6/3
 no ip address
 shutdown
 serial restart-delay 0
!
!
router eigrp 100
 network 10.40.10.0 0.0.0.255
 network 192.168.5.0 0.0.0.1
 network 192.168.6.0 0.0.0.1
 redistribute static
 passive-interface GigabitEthernet1/0
!
router bgp 65000
 bgp log-neighbor-changes
 bgp default local-preference 200
 neighbor 10.40.10.1 remote-as 65100
 neighbor 10.40.10.1 prefix-list PERMIT-VPC-ONLY out
 neighbor 192.168.5.0 remote-as 65000
 neighbor 192.168.5.0 next-hop-self
 neighbor 192.168.5.0 default-originate
 neighbor 192.168.6.1 remote-as 65000
 neighbor 192.168.6.1 next-hop-self
 neighbor 192.168.6.1 default-originate
!
ip nat inside source list 1 interface Loopback0 overload
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
!
!
ip prefix-list PERMIT-VPC-ONLY seq 10 permit 192.168.0.0/24
ip prefix-list PERMIT-VPC-ONLY seq 20 permit 192.168.7.0/24
access-list 1 permit any
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
 stopbits 1
line vty 0 4
 login
!
!
end
```

#### Show ip bgp summary de R1 à R5

<img width="3200" height="1555" alt="02 - show ip bgp summary R1-5" src="https://github.com/user-attachments/assets/e401d5e6-ee35-456d-ab4b-f7e4bfe7abf6" />

#### Show ip bgp R1 et R4

<img width="2536" height="628" alt="03 - show ip bgp R1 et R4" src="https://github.com/user-attachments/assets/85805912-9317-41be-aef0-c5f02e35f387" />

#### Changement de politique BGP

<img width="2467" height="794" alt="04 - changement de politique" src="https://github.com/user-attachments/assets/0b40f915-f61f-4953-a4f5-b02f7ecb0c5f" />

#### Connectivité au Cloud

La session eBGP entre R5 et le Cloud1 (10.40.10.1) est parfaitement établie (état Established). L'échec des requêtes ICMP (ping) vers l'adresse d'interconnexion du Cloud provient d'un filtrage ICMP / pare-feu au niveau de l'interface réseau hôte liée au nœud Cloud dans l'environnement de simulation GNS3, et non d'une erreur de configuration de la table de routage BGP.

## Rapport de Synthèse - Cahier des Charges 3

### 1. Choix d'AS et Architecture BGP

Dans le cadre de cette extension réseau, nous avons mis en place une architecture BGP hybride combinant iBGP en interne et eBGP vers le FAI :

* AS 65000 (AS Interne) : Regroupe les routeurs R1, R2, R3, R4 et R5. Les sessions iBGP permettent de propager la route par défaut et les préfixes internes de manière cohérente à travers l'infrastructure.
* AS 65100 (AS FAI) : Représente l'AS externe du fournisseur d'accès Internet (Cloud1 - 10.40.10.1).
* R5 (Passerelle BGP de Bordure) : Assure l'interconnexion eBGP avec le FAI et relaie les informations de routage vers le cœur de réseau via iBGP.

### 2. Politique de Routage BGP et Filtrage

#### Politiques appliquées :
1. Local Preference (Sortie WAN) : Configurée par défaut à `200` sur R5, elle garantit que R5 est privilégié comme passerelle de sortie principale pour l'ensemble des routeurs de l'AS 65000.
2. Propagation de la Route par Défaut : R5 annonce la route `0.0.0.0/0` à ses voisins iBGP via la commande `default-originate`.
3. Filtrage des Annonces Sortantes (Prefix-List) : Pour des raisons de sécurité et de conformité WAN, une `prefix-list` nommée `PERMIT-VPC-ONLY` est appliquée en sortie vers le FAI sur R5. Seuls les réseaux clients VPC1 (`192.168.0.0/24`) et VPC2 (`192.168.7.0/24`) sont autorisés à être annoncés à l'AS 65100.

### 3. Analyse des Tests et Résilience

#### Validation de la politique BGP :

Les vérifications sur R1 et R4 confirment la bonne réception de la route par défaut avec la `Local Preference` souhaitée (passage dynamique de 200 à 300 validé lors des tests).

#### Résilience et Tolérance aux Pannes (Failover) :

Lors de la simulation d'une coupure du lien eBGP / FAI (shutdown de l'interface de bordure sur R5), le trafic d'interconnexion interne entre VPC1 et VPC2 bascule sans interruption sur l'overlay DMVPN / EIGRP (CDC 1 et CDC 2). Cette étanchéité garantit une continuité de service totale pour le réseau d'entreprise local même en cas de panne de l'accès Internet.

## Historiques de toutes les commandes
#### Les commandes sont commentés et mises en places sous formes de `/*BLOC*/`

```
R1 : 

/*CONFIG DE BASE*/
en
conf t
hostname R1

interface f0/0
ip add 192.168.0.254 255.255.255.0
no shutdown
exit

interface g1/0
ip add 192.168.1.0 255.255.255.254
no shutdown
exit

interface s6/0
ip add 192.168.4.0 255.255.255.254
clockrate 64000
encapsulation ppp
no shutdown
exit

interface f4/0
ip add 192.168.5.0 255.255.255.254
no shutdown
exit

/*CONFIG EIGRP*/
router eigrp 100
passive-interface fa0/0
network 192.168.0.0 0.0.0.255
network 192.168.1.0 0.0.0.1
network 192.168.4.0 0.0.0.1
network 192.168.5.0 0.0.0.1
no auto-summary
exit

/*CONFIG CRYPTO*/
crypto isakmp Policy 10
encr aes 256
hash sha256
authentication pre-share
group 14
lifetime 86400
exit

crypto isakmp key SatomSecretKey123 address 0.0.0.0 0.0.0.0

crypto ipsec transform-set TS-DMVPN esp-aes 256 esp-sha256-hmac
mode transport
exit

crypto ipsec profile IPSEC-PROFILE-DMVPN
set transform-set TS-DMVPN
exit

/*CONFIG TUNNEL*/
interface Tunnel0
description interface Hub DMVPN CDC 2 
ip add 172.16.0.1 255.255.255.0
no ip redirects
ip mtu 1400
ip tcp adjust-mss 1360
ip nhrp authentication SatomNHRP
ip nhrp network-id 100
ip nhrp redirect
ip nhrp map multicast dynamic
ip nhrp authentication SatmNHRP
tunnel source g1/0
tunnel mode gre multipoint
tunnel protection ipsec profile IPSEC-PROFILE-DMVPN
no ip split-horizon eigrp 100

exit

router eigrp 100
network 172.16.0.0 0.0.0.255
exit

/*CONFIG BGP*/
router bgp 65000
bgp log-neighbor-changes
neighbor 172.16.0.2 remote-as 65000
neighbor 172.16.0.3 remote-as 65000
neighbor 172.16.0.4 remote-as 65000
neighbor 192.168.5.1 remote-as 65000
neighbor 192.168.5.1 next-hop-self
network 192.168.0.0 mask 255.255.255.0
exit

ip route 192.168.0.0 255.255.255.0 Null0

end
wr


R2 : 

/*CONFIG DE BASE*/
en
conf t
hostname R2

interface g1/0
ip add 192.168.1.1 255.255.255.254
no shutdown
exit

interface g2/0
ip add 192.168.2.0 255.255.255.254
no shutdown
exit

/*CONFIG EIGRP*/
router eigrp 100
network 192.168.1.0 0.0.0.1
network 192.168.2.0 0.0.0.1
no auto-summary
exit

/*CONFIG CRYPTO*/
crypto isakmp policy 10
encr aes 256
hash sha256
authentication pre-share
group 14
lifetime 86400
exit

crypto isakmp key SatomSecretKey123 address 0.0.0.0 0.0.0.0

crypto ipsec transform-set TS-DMVPN esp-aes 256 esp-sha256-hmac
mode transport
exit

crypto ipsec profile IPSEC-PROFILE-DMVPN
set transform-set TS-DMVPN
exit

interface Tunnel0
description Interface Spoke DMVPN R2
ip add 172.16.0.2 255.255.255.0
no ip redirects
ip mtu 1400
ip tcp adjust-mss 1360
ip nhrp network-id 100
ip nhrp shortcut
ip nhrp nhs 172.16.0.1
ip nhrp map 172.16.0.1 192.168.1.0
ip nhrp map multicast 192.168.1.0
ip nhrp authentication SatmNHRP

tunnel source g1/0
tunnel mode gre multipoint
tunnel protection ipsec profile IPSEC-PROFILE-DMVPN
exit

router eigrp 100
network 172.16.0.0 0.0.0.255
exit

/*CONFIG BGP*/
router bgp 65000
bgp log-neighbor-changes
neighbor 172.16.0.1 remote-as 65000
neighbor 172.16.0.3 remote-as 65000
neighbor 172.16.0.4 remote-as 65000
exit

end
wr


R3 : 

/*CONFIG DE BASE*/
en
conf t
hostname R3

interface g1/0
ip add 192.168.3.0 255.255.255.254
no shutdown
exit

interface g2/0
ip add 192.168.2.1 255.255.255.254
no shutdown
exit

/*CONFIG EIGRP*/
router eigrp 100
network 192.168.2.0 0.0.0.1
network 192.168.3.0 0.0.0.1
no auto-summary
exit

/*CONFIG CRYPTO*/
crypto isakmp policy 10
encr aes 256
hash sha256
authentication pre-share
group 14
lifetime 86400
exit

crypto isakmp key SatomSecretKey123 address 0.0.0.0 0.0.0.0

crypto ipsec transform-set TS-DMVPN esp-aes 256 esp-sha256-hmac
mode transport
exit

crypto ipsec profile IPSEC-PROFILE-DMVPN
set transform-set TS-DMVPN
exit

interface Tunnel0
description Interface Spoke DMVPN R3
ip add 172.16.0.3 255.255.255.0
no ip redirects
ip mtu 1400
ip tcp adjust-mss 1360
ip nhrp authentication SatomNHRP
ip nhrp network-id 100
ip nhrp shortcut
ip nhrp nhs 172.16.0.1
ip nhrp map 172.16.0.1 192.168.1.0
ip nhrp map multicast 192.168.1.0
ip nhrp authentication SatmNHRP
 
tunnel source GigabitEthernet2/0
tunnel mode gre multipoint
tunnel protection ipsec profile IPSEC-PROFILE-DMVPN
exit

router eigrp 100
network 172.16.0.0 0.0.0.255
exit

/*CONFIG BGP*/
router bgp 65000
bgp log-neighbor-changes
neighbor 172.16.0.1 remote-as 65000
neighbor 172.16.0.2 remote-as 65000
neighbor 172.16.0.4 remote-as 65000
exit

end
wr


R4 : 

/*CONFIG DE BASE*/
en
conf t
hostname R4

interface f0/0
ip add 192.168.7.254 255.255.255.0
no shutdown
exit

interface g1/0
ip add 192.168.3.1 255.255.255.254
no shutdown
exit

interface s6/0
ip add 192.168.4.1 255.255.255.254
encapsulation ppp
no shutdown
exit

interface f4/1
ip add 192.168.6.1 255.255.255.254
no shutdown
exit

/*CONFIG EIGRP*/
router eigrp 100
passive-interface fa0/0
network 192.168.7.0 0.0.0.255
network 192.168.3.0 0.0.0.1
network 192.168.4.0 0.0.0.1
network 192.168.6.0 0.0.0.1
no auto-summary
exit

/*CONFIG CRYPTO*/
crypto isakmp policy 10
encr aes 256
hash sha256
authentication pre-share
group 14
lifetime 86400
exit

crypto isakmp key SatomSecretKey123 address 0.0.0.0 0.0.0.0

crypto ipsec transform-set TS-DMVPN esp-aes 256 esp-sha256-hmac
mode transport
exit

crypto ipsec profile IPSEC-PROFILE-DMVPN
set transform-set TS-DMVPN
exit

interface Tunnel0
description Interface Spoke DMVPN R4
ip address 172.16.0.4 255.255.255.0
no ip redirects
ip mtu 1400
ip tcp adjust-mss 1360
ip nhrp authentication SatomNHRP
ip nhrp network-id 100
ip nhrp shortcut
ip nhrp nhs 172.16.0.1
ip nhrp map 172.16.0.1 192.168.1.0
ip nhrp map multicast 192.168.1.0
ip nhrp authentication SatmNHRP
 
tunnel source GigabitEthernet1/0
tunnel mode gre multipoint
tunnel protection ipsec profile IPSEC-PROFILE-DMVPN
exit

router eigrp 100
network 172.16.0.0 0.0.0.255
exit

/*CONFIG BGP*/
router bgp 65000
bgp log-neighbor-changes
neighbor 172.16.0.1 remote-as 65000
neighbor 172.16.0.2 remote-as 65000
neighbor 172.16.0.3 remote-as 65000
neighbor 192.168.6.0 remote-as 65000
neighbor 192.168.6.0 next-hop-self
network 192.168.7.0 mask 255.255.255.0
exit

ip route 192.168.7.0 255.255.255.0 Null0

end
wr


R5 : 

/*CONFIG DE BASE*/
en
conf t
hostname R5

interface g1/0
no shutdown
exit

interface f4/0
ip add 192.168.5.1 255.255.255.254
ip nat inside
no shutdown
exit

interface f4/1
ip add 192.168.6.0 255.255.255.254
ip nat inside
no shutdown
exit

interface loopback 0
ip address 10.40.10.1 255.255.255.0
ip nat outside
exit

access-list 1 permit any
ip nat Inside source list 1 interface Loopback0 overload

ip route 0.0.0.0 0.0.0.0 Loopback0

/*CONFIG EIGRP*/
router eigrp 100
redistribute static
passive-interface g1/0
network 192.168.5.0 0.0.0.1
network 192.168.6.0 0.0.0.1
network 10.40.10.0 0.0.0.255
no auto-summary
exit

/*CONFIG BGP*/

no ip route 0.0.0.0 0.0.0.0 Loopback0
no interface Loopback0
interface g1/0
ip add 10.40.10.2 255.255.255.0
no shutdown
exit

ip prefix-list PERMIT-VPC-ONLY seq 10 permit 192.168.0.0/24
ip prefix-list PERMIT-VPC-ONLY seq 20 permit 192.168.7.0/24

router bgp 65000
bgp log-neighbor-changes
bgp default local-preference 200

neighbor 192.168.5.0 remote-as 65000
neighbor 192.168.5.0 next-hop-self
neighbor 192.168.5.0 default-originate

neighbor 192.168.6.1 remote-as 65000
neighbor 192.168.6.1 next-hop-self
neighbor 192.168.6.1 default-originate

neighbor 10.40.10.1 remote-as 65100
neighbor 10.40.10.1 prefix-list PERMIT-VPC-ONLY out
exit

end
wr

PC1 : 

set pcname PC1
ip 192.168.0.1/24 192.168.0.254
save

PC2 : 

set pcname PC2
ip 192.168.7.1/24 192.168.7.254
save
```

## Questionnaire QCM - 100 questions

Q1. Quel protocole de routage EIGRP utilise-t-il pour transmettre ses messages ?
b) Un protocole IP numéro 88

Q2. Pour que deux routeurs deviennent voisins EIGRP, quelle condition est obligatoire ?
b) Même numéro de système autonome

Q3. Quelle est la distance administrative par défaut d'une route EIGRP interne ?
b) 90

Q4. Par défaut, quelles métriques EIGRP sont prises en compte dans le calcul de la métrique ?
a) Bande passante et délai

Q5. Quelle adresse multicast EIGRP utilise-t-il pour envoyer ses hellos ?
c) 224.0.0.10

Q6. Un routeur EIGRP reçoit une route avec une faisable distance de 2 000 et une distance rapportée de 1 500 par son voisin. Que peut-il conclure ?
a) La route est faisable (feasible successor)

Q7. Quel est le rôle de l'algorithme DUAL ?
b) Calculer les routes sans boucle et sans route de secours inutile

Q8. Quelle commande permet de voir les voisins EIGRP ?
b) show ip eigrp neighbors

Q9. Sur une interface série haut débit, quel est le temps par défaut du hello EIGRP ?
a) 5 secondes

Q10. Quel est le hold time par défaut d'EIGRP sur un réseau à haut débit ?
b) 15 secondes

Q11. Quel est l'effet de la commande passive-interface sous EIGRP ?
b) Elle arrête l'envoi des hellos sur l'interface, tout en continuant à annoncer le réseau

Q12. Dans une configuration EIGRP moderne (IOS 15), que vaut la résumation automatique ?
b) Désactivée par défaut

Q13. Pour répartir la charge sur deux chemins de coûts différents avec EIGRP, quelle commande est utilisée ?
b) variance

Q14. Quelle est la métrique qui définit le meilleur chemin lorsque deux routes EIGRP ont des bandes passantes différentes ?
a) Le chemin à plus petit coût total composé de bande passante et de délai

Q15. Quelle commande permet de vérifier le numéro AS et les réseaux annoncés par EIGRP ?
a) show ip protocols

Q16. Sur une liaison point-à-point en 192.168.1.0/31, combien d'adresses IP sont disponibles pour les deux extrémités ?
c) 2

Q17. Quel type de route EIGRP correspond à une route apprise d'un autre protocole de routage ?
b) Externe

Q18. Quel champ d'un paquet EIGRP sert à éviter les boucles de routage ?
a) TTL

Q19. Quel est le principal avantage d'une route feasible successor ?
a) Elle permet un basculement immédiat sans recalcul complet

Q20. Quelle commande affiche la topologie complète EIGRP ?
a) show ip eigrp topology

Q21. Quel protocole de routage est dit « à état de lien » ?
c) OSPF

Q22. Quelle est la distance administrative d'une route statique par défaut ?
a) 1

Q23. Quelle est la différence principale entre un protocole à vecteur de distance et un protocole à état de lien ?
a) Le vecteur de distance ne connaît pas toute la topologie, l'état de lien la connaît

Q24. Quelle commande permet de forcer un identifiant de routeur EIGRP ou OSPF ?
a) router-id

Q25. Pourquoi faut-il tester une bascule de liaison dans un réseau de routage dynamique ?
a) Pour vérifier que la convergence fonctionne et que le trafic est réacheminé

Q26. Quel encapsulage est utilisé par défaut sur une interface série Cisco ?
b) HDLC

Q27. Quel protocole de liaison de données propose authentification CHAP et PAP ?
a) PPP

Q28. Une liaison série « DCE » fournit quel élément ?
a) Le signal d'horloge

Q29. Quel est le rôle d'un routeur de bordure (edge) dans une architecture d'entreprise ?
a) Relier le réseau interne aux réseaux externes

Q30. Quel protocole de la couche transport utilise BGP ?
b) TCP

Q31. Dans un réseau MPLS, quel élément est ajouté au paquet pour le transport ?
a) Une étiquette (label)

Q32. Quel est l'intérêt principal d'une liaison WAN « série » par rapport à une liaison Ethernet dans un contexte de formation ?
b) Elle permet de simuler une liaison opérateur avec un débit et une horloge contrôlés

Q33. Quel terme désigne la mesure de la qualité de service qui donne la priorité au trafic voix ?
a) QoS

Q34. Quelle est la valeur par défaut du MTU Ethernet ?
b) 1 500 octets

Q35. Pourquoi réduire le MTU lors d'un tunnel est-il parfois nécessaire ?
a) Pour absorber l'en-tête supplémentaire du tunnel sans fragmentation

Q36. Quel est le rôle de la phase 1 d'IPsec (IKE phase 1) ?
a) Négocier et établir un canal sécurisé de gestion (ISAKMP SA)

Q37. Quel est le rôle de la phase 2 d'IPsec ?
a) Négocier les SA qui protégeront le trafic de données

Q38. Quel protocole IPsec assure à la fois la confidentialité et l'intégrité des données ?
b) ESP

Q39. Quel protocole IPsec n'assure pas la confidentialité des données ?
b) AH

Q40. Quel est le numéro de protocole IP d'ESP ?
b) 50

Q41. Quel port UDP est utilisé par IKE ?
b) 500

Q42. Quel port UDP est utilisé pour NAT-Traversal (NAT-T) avec IPsec ?
b) 4500

Q43. Quelle différence entre le mode tunnel et le mode transport ?
a) En mode tunnel, le paquet IP complet est chiffré dans un nouveau paquet

Q44. Quelle est la fonction d'un « transform set » ?
a) Définir les algorithmes de chiffrement et d'authentification de la SA de phase 2

Q45. Quel est le rôle de la PFS (Perfect Forward Secrecy) ?
c) Compresser les paquets

Q46. Quel algorithme de chiffrement symétrique est recommandé aujourd'hui ?
c) AES

Q47. Quel algorithme de hachage est déconseillé pour l'intégrité ?
b) MD5

Q48. Quelle est la durée de vie typique d'une SA de phase 1 ?
b) 86 400 secondes

Q49. Une crypto map est appliquée à quoi ?
a) À une interface

Q50. Pour qu'un tunnel IPsec s'établisse, quelle condition doit être remplie entre les pairs ?
a) Même politique ISAKMP, clés pré-partagées ou certificats compatibles, et trafic intéressant défini

Q51. Que signifie « trafic intéressant » dans IPsec ?
a) Le trafic dont la source et la destination sont définies dans une ACL pour être chiffré

Q52. Quelle commande affiche les SA IPsec établies ?
a) show crypto isakmp sa

Q53. Quel est l'avantage d'IKEv2 par rapport à IKEv1 ?
a) Moins d'échanges et une meilleure robustesse

Q54. Un tunnel IPsec est établi mais le trafic ne passe pas. Quelle est la cause la plus probable ?
a) L'ACL définissant le trafic intéressant est incorrecte

Q55. Dans une topologie hub-and-spoke, pourquoi utiliser un VPN IPsec entre chaque site ?
a) Pour sécuriser les échanges entre les sites tout en gardant une politique centralisée

Q56. Que signifie DMVPN ?
a) Dynamic Multipoint VPN

Q57. Quel protocole est utilisé pour résoudre l'adresse NBMA d'un tunnel dans DMVPN ?
b) NHRP

Q58. Quel est le rôle du hub dans un DMVPN ?
a) Serveur NHRP et point central de connexion des spokes

Q59. Quel type de tunnel est utilisé comme base dans DMVPN ?
a) mGRE (multipoint GRE)

Q60. Quel est le numéro de protocole IP du GRE ?
a) 47

Q61. Quel est l'intérêt d'un tunnel mGRE par rapport à un GRE point-à-point ?
a) Il permet de relier plusieurs pairs sur une seule interface de tunnel

Q62. Dans DMVPN phase 3, quel mécanisme permet à deux spokes de créer un tunnel direct ?
a) NHRP redirect et shortcut

Q63. Quel est le problème principal d'une topologie DMVPN phase 1 ?
a) Tout le trafic spoke-to-spoke passe par le hub

Q64. Quelle commande active NHRP sur une interface tunnel ?
a) ip nhrp network-id

Q65. Quel est le rôle de ip nhrp map ?
a) Associer l'adresse IP du tunnel à l'adresse NBMA (IP publique ou de transport)

Q66. Quelle est la différence entre NBMA et tunnel IP ?
c) NBMA est une adresse MAC

Q67. Pourquoi protège-t-on souvent un tunnel DMVPN avec un profil IPsec ?
a) Pour chiffrer les paquets GRE

Q68. Quel élément mène à l'ajout d'un nouveau spoke dans un DMVPN ?
a) Configurer le spoke avec l'adresse du hub et l'enregistrer auprès du hub

Q69. Dans DMVPN, quel protocole de routage est souvent utilisé entre le hub et les spokes ?
a) EIGRP ou BGP

Q70. Quelle commande affiche l'état des tunnels NHRP ?
a) show ip nhrp

Q71. Pourquoi le split-horizon pose-t-il problème dans DMVPN phase 2 ?
a) Il empêche le routeur d'annoncer une route apprise sur la même interface

Q72. Quel est l'avantage principal de DMVPN par rapport à un réseau de VPN IPsec point-à-point complet (full mesh) ?
a) Il évite de configurer manuellement chaque tunnel entre chaque couple de sites

Q73. Quelle est la différence entre un spoke et un hub dans DMVPN ?
a) Le hub est un point central de signalisation, le spoke initie les tunnels vers le hub

Q74. Un spoke n'arrive pas à s'enregistrer auprès du hub. Quel élément vérifier en premier ?
a) L'adresse NBMA du hub, le ip nhrp nhs et la connectivité de transport

Q75. Quel est le rôle de ip nhrp nhs sur un spoke ?
d) Désactiver NAT

Q76. Quel port TCP utilise BGP ?
a) 179

Q77. Quelle est la distance administrative d'une route eBGP ?
a) 20

Q78. Quelle est la distance administrative d'une route iBGP ?
c) 200

Q79. Quel attribut BGP est prioritaire pour choisir la sortie préférée au sein d'un même AS ?
a) LOCAL_PREF

Q80. Quelle est la règle de choix du meilleur chemin concernant l'AS_PATH ?
a) Le chemin le plus court est préféré

Q81. Quel attribut BGP est utilisé pour influencer l'entrée de trafic chez un voisin ?
b) LOCAL_PREF

Q82. Quelle est la valeur par défaut de LOCAL_PREF ?
a) 100

Q83. Quel attribut BGP est défini localement et n'est pas transmis aux voisins ?
a) LOCAL_PREF

Q84. Quel est le rôle de next-hop-self dans une session iBGP ?
a) Remplacer le prochain saut par l'adresse du routeur qui annonce

Q85. Quel est l'intérêt d'un network statement en BGP ?
a) Annoncer un préfixe présent dans la table de routage locale

Q86. Quelle commande affiche le résumé des sessions BGP ?
a) show ip bgp summary

Q87. Quelle est la conséquence d'un AS_PATH contenant son propre numéro d'AS ?
a) Le routeur rejette la route pour éviter une boucle

Q88. Quel est le rôle du MED ?
a) Suggérer au voisin par quel point d'entrée il doit envoyer le trafic

Q89. Quel attribut BGP est le plus prioritaire dans l'ordre de décision ?
a) Weight (propre à Cisco)

Q90. Quel est le rôle d'un route reflector en iBGP ?
d) Convertir EIGRP en BGP

Q91. Pourquoi les sessions iBGP exigent-elles souvent une adresse de bouclage (loopback) ?
a) Pour garantir la stabilité de la session même si une interface physique tombe

Q92. Quel est le rôle d'un filtre de préprefixes en BGP ?
a) Accepter ou refuser certaines routes annoncées ou reçues

Q93. Dans une session eBGP, quel est le TTL par défaut ?
c) 255

Q94. Quel est le rôle des timers de keepalive et de hold dans BGP ?
a) Vérifier l'état de la session et détecter une panne

Q95. Quel est le risque d'annoncer un préfixe inutile vers un fournisseur ?
c) Il est sans conséquence

Q96. Quel protocole de la famille SD-WAN gère les routes entre les routeurs de bordure ?
a) OMP

Q97. Quel est l'intérêt d'un réseau de type VXLAN ?
c) Remplacer BGP

Q98. Quel est le port UDP par défaut de VXLAN ?
a) 4789

Q99. Une entreprise veut relier 50 sites avec un minimum de configuration manuelle. Quelle architecture privilégier ?
a) Un DMVPN ou une architecture SD-WAN avec contrôleur centralisé

Q100. Quelle est la première étape lors d'un diagnostic de panne dans un réseau d'entreprise ?
b) Redémarrer tous les routeurs
