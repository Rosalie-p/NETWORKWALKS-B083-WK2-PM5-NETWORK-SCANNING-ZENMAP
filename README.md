# NETWORKWALKS-B083-WK2-PM5-NETWORK-SCANNING-ZENMAP
## Network Scanning with Zenmap — README

This guide documents the WK2-PM5 Network Scanning task: installing Zenmap (the official GUI for Nmap) on a Windows PC, discovering live hosts on the local network, and exporting a network topology diagram.

## Task Requirements
Windows PC (host machine)
Zenmap, downloaded from the official source: https://nmap.org/download.html
Local home network access
Setup & Tasks Performed
## 1. Install Zenmap

Downloaded and installed Zenmap (bundled with Nmap and the Npcap packet-capture driver) from the official Nmap site.

## 2. Find local IP address & LAN subnet
ipconfig
Item	Value
IPv4 Address	192.168.5.193
Subnet Mask	255.255.255.0
Default Gateway	192.168.5.1
Derived subnet	192.168.5.0/24
## 3. Find live hosts on the subnet

In Zenmap: Target = 192.168.5.0/24, Profile = Ping scan, then Scan.

nmap -sn 192.168.5.0/24


## 4. How many hosts are live?

3 hosts were found live (including the scanning PC).

## 5. IP addresses of the live hosts
192.168.5.1 — network gateway / router
192.168.5.72 — another device on the network
192.168.5.193 — scanning PC (own device)
## 6. MAC addresses of the live hosts
Host	MAC Address	Source
192.168.5.72	6A:A8:51:47:D8:2D	Returned directly by the Nmap ping scan
192.168.5.193 (own PC)	AA-B7-CD-85-6C-DA	Obtained via ipconfig /all (a host can't see its own MAC through a scan of itself)
192.168.5.1 (gateway)	Not returned	Some routers don't respond with a MAC to a standard ARP/ping sweep
## 7. Topology diagram (saved as PDF)

Opened the Topology tab in Zenmap, enabled the legend, and exported the diagram via Save Graphic → PDF.



Notes

Ping-scanning a network is a form of active host discovery — unlike passive footprinting, this sends real ARP/ICMP probes onto the network. It was performed only against my own home network, which I own and am authorized to scan.

Based on the "Network Scanning with Zenmap" task from Networkwalks Academy — www.networkwalks.com
