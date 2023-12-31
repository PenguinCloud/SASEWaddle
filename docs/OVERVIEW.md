# Components
## Open Source Components
* NGINX Proxy w/ ModProxy
* VyOS - Client VPN / Firewall
  * IPSEC
  * OpenVPN
* Tobagining - S2S / Cluster 2 Cluster Wireguard 
* ClamAV
* Zeek
* Suricata
* Gluu & Gluu Proxy
* SOF-ELK (Logging)
* Rookery - VDI
* Cuckoo (sandbox)

## Premium Components
* PenguinSASE Agent - GoLang based agent which can handle auth and enforcement and L4SSL tunnels
* PenguinSASE Unified Console - Django based console
* PenguinSASE in-line / out of band detection for Suricata toggle

# Overview of flow
1. Traffic comes in via VPN, Direct Proxy, or VDI 
2. Supported protocols are routed through NGINX
3. NGINX routes a copy of traffic to Zeek and Surricata and adds to the access log ... out of band
4. Zeek and Suricata analyze and report executables and any bad traffic hits
5. Traffic identified by Zeek and Suricata are added to NGINX filters and VyOS
6. Bypassed protocols (NGINX doesnt support) are still routed through Suricata and Zeek
7. Traffic is allowed forward if not in the NGINX and VyOS block list
