Raspberry Pi Network Security \& Monitoring Stack



System Overview

A Raspberry Pi is used as the central network control node providing:

Network-wide DNS filtering

Secure VPN access

DHCP services

Network monitoring and visualization



Components used:

Pi-hole

WireGuard

Prometheus

Grafana



Step 1

Check IP address of the Raspberry Pi.  -ip a This ip will be used for all services



Step 2 

install Pihole  -curl -sSL https://install.pi-hole.net | bash

During installation:  Upstream DNS Provider → Cloudflare->Blocklist → StevenBlack Unified Hosts->Query Logging → Enabled

After installation: http://<raspberry-pi-ip>/admin



Step 3

Configure router DNS

Primary DNS → 192.168.0.103



Step 4

Setting->DHCP

Enable DHCP and configure

Start IP → 192.168.0.100

End IP → 192.168.0.199

Router → 192.168.0.1



Step 5

Install PiVPN- curl -L https://install.pivpn.io | bash

VPN protocol → WireGuard

Default port → 51820

DNS provider → Pi-hole



Step 6

Create VPN Client

vpn profileb - pivpn add

ex client name - samarth\_phone

verify clients - pivpn list



Step 7 

Verify Guard interface

sudo wg



Step 8 

sudo apt update



Step 9 

Install Prometheus

sudo apt install prometheus -y

Start Prometheus service - sudo systemctl enable prometheus    sudo systemctl start Prometheus

verify status - systemctl status Prometheus



Step 10 

install node explorer-  sudo apt install prometheus-node-exporter -y

verify-  systemctl status prometheus-node-exporter



Step 11 

Configure Prometheus- systemctl status prometheus-node-exporter

Add node explorer target- 

scrape\_configs:

&nbsp; - job\_name: node\_exporter

&nbsp;   static\_configs:

&nbsp;     - targets: \['localhost:9100']

Then restart it - sudo systemctl restart Prometheus



Step 12

Install Grafana.

add repo key-  sudo mkdir -p /etc/apt/keyrings

&nbsp;              wget -q -O - https://packages.grafana.com/gpg.key | sudo tee /etc/apt/keyrings/grafana.gpg

add repo- 

&nbsp;       echo "deb \[signed-by=/etc/apt/keyrings/grafana.gpg] https://packages.grafana.com/oss/deb stable main" | sudo tee       /etc/apt/sources.list.d/grafana.list

update packages- sudo apt update

install grafana- sudo apt install grafana -y

start Grafana server- sudo systemctl enable grafana-server   sudo systemctl start grafana-server

verify- systemctl status grafana-server

open Grafana dashboard - http://<pi-ip>:3000



Step 13

inside Grafana dashboard:Connections → Data Sources → Add Data Source->select Prometheus

set URL- http://localhost:9090



Step 14

Import monitoring dashboards

dashboard ID-1860 (CPU and mem usage , disk usage , traffic)

dashboard ID-10176 (DNS queries, blocked domains , top clients)



Step15

Verify system

pihole- http://192.168.0.103/admin

Grafana - http://192.168.0.103:3000

prometheus- http://192.168.0.103:9090

test ad blocking -ads.google.com   doubleclick.net



Final result The Raspberry Pi now functions as a complete home network security and monitoring server.
Linux server administration

network infrastructure deployment

DNS architecture

VPN configuration

observability and monitoring

system performance analysis

