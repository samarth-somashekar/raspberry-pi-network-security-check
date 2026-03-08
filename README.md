# Raspberry Pi Network Security & Monitoring Stack

## Overview
This project builds a home network security and monitoring system using a Raspberry Pi.

The Raspberry Pi acts as a central network controller providing:

- DNS-based ad and tracker blocking
- Secure remote VPN access
- Network monitoring and observability

## Architecture

Internet  
   │  
Router (TP-Link Archer C5)  
   │  
Raspberry Pi 5  

Services running on Raspberry Pi:

- Pi-hole (DNS filtering)
- WireGuard VPN
- Prometheus (metrics collection)
- Grafana (monitoring dashboards)

## Features

- Network-wide ad and tracker blocking
- Secure remote access using VPN
- Real-time monitoring dashboards
- DNS query logging and analysis
- System metrics visualization

## Technologies Used

- Raspberry Pi 5
- Pi-hole
- WireGuard
- Prometheus
- Grafana
- Linux
