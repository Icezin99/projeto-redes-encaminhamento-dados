# Data Forwarding Project

Practical project developed within the scope of the Data Forwarding course of the Bachelor's Degree in Computer Engineering (Networking and Systems Administration Track) at ISEC.

## Network Overview

The project consisted of designing and configuring a network infrastructure for a large-scale resort. The architecture followed a Hub-and-Spoke model, using the Central Administrative Building (CAB) as the core responsible for aggregating traffic, summarizing routes, and applying core policies.

![Network Topology](topologia/topologia-ED.png)

The network was divided into three main sectors:
- **West Sector:** Leisure & Sports Area (LSA) running OSPF, and Operational Services (OS) running EIGRP.
- **East Sector:** Central Administrative Building (CAB) with OSPF, Bungalows & Villas (BV) with EIGRP, and the Restaurant with RIPv2.
- **North Sector:** Conference Center (CC) with OSPFv3, Main Hotel (HP) with OSPF, and the Spa & Wellness Center (SWC) with RIPv2.

## What Was Implemented

- **Dynamic Routing:** Configuration of multiple protocols simultaneously (OSPF, OSPFv3, EIGRP, and RIPv2) depending on the network zone.
- **Internet Gateway:** NAT implementation for address translation, featuring a primary 1 Gbps link at the CAB and a *backup* link (100 Mbps) at the Operational Services.
- **Traffic Policies (PBR):** Creation of *Policy-Based Routes* and *Access Lists* in the Spa & Wellness Center to enforce specific paths for traffic.
- **Filters:** Use of *Prefix-lists* in Operational Services to control and limit the routes that were advertised.
- **Remote Access:** Telnet configuration on routers with single-session restriction and custom welcome messages per device.

## ⚠️ Notes and Areas for Improvement

- **External Connectivity:** The configuration of the internet *backup* path in Operational Services presented limitations in return traffic forwarding, identified as an area for optimization in future resilience testing.

## Repository Contents

- [`topologia/`](topologia/) - Image containing the logical network topology and respective simulation files.
- [`excel/`](excel/) - Detailed IP addressing table (with complete subnet planning).
