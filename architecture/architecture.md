\# Network Architecture



The Raspberry Pi acts as the central network control node for the home network.



Internet

&nbsp;  │

Router (TP-Link Archer C5)

&nbsp;  │

Raspberry Pi 5

&nbsp;├── Pi-hole DNS filtering

&nbsp;├── DHCP Server

&nbsp;├── WireGuard VPN

&nbsp;├── Prometheus Metrics

&nbsp;└── Grafana Monitoring

&nbsp;  │

Home Devices

&nbsp;├── Laptop

&nbsp;├── Phone

&nbsp;├── Smart TV

&nbsp;└── IoT Devices

