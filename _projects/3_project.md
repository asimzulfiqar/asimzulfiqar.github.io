---
layout: page
title: Enterprise Network Monitoring Platform
description: A comprehensive Grafana Cloud-based monitoring solution for multi-vendor network infrastructure with centralized metrics collection, log aggregation, and intelligent alerting across Huawei, Mikrotik, and Cisco equipment.
img: assets/img/grafana-dashboard.png
importance: 1
category: work
related_publications: false
---

A production-grade monitoring infrastructure delivering unified visibility into enterprise network operations, providing real-time performance metrics, automated incident detection, and multi-channel alerting across heterogeneous network devices including routers, switches, and optical line terminals.

## System Architecture

The platform integrates Prometheus for time-series metrics collection, Loki for centralized log aggregation, and Grafana Cloud for visualization and alerting. The architecture supports multi-vendor network equipment through standardized monitoring protocols including SNMP, syslog, and vendor-specific exporters, providing a single pane of glass for network operations.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/grafana-dashboard.png" title="Network Monitoring Dashboard" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Grafana dashboard displaying real-time server metrics including CPU utilization, memory usage, network traffic, and disk I/O across monitored infrastructure with 10.9 weeks of uptime.
</div>

## Key Components

**Metrics Collection Infrastructure**: Deployed Prometheus with 15-second scrape intervals collecting metrics from SNMP Exporter for network devices, Node Exporter for Linux servers, and Windows Exporter for Windows systems. Configured Grafana PDC (Private Data Source Connect) agent to establish secure tunnel between on-premise Prometheus and Grafana Cloud, enabling hybrid cloud monitoring architecture.

**Log Aggregation Pipeline**: Implemented Loki with Promtail agents for centralized syslog collection from Huawei NE40 routers and Mikrotik switches. Configured rsyslog for remote log forwarding and log rotation with 7-day retention policy, enabling efficient troubleshooting and compliance auditing across distributed network infrastructure.

**Multi-Channel Alerting System**: Designed notification templates and contact points for Email and Telegram delivery with Grafana OnCall integration. Created alert rules monitoring link status, LACP port health, optical power levels, and connectivity with customizable evaluation intervals and threshold-based triggering.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/alerts.png" title="Alert Rules Dashboard" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Grafana alert rules dashboard showing 11 active monitoring rules including link down detection, port status monitoring, and connectivity checks with real-time health status and evaluation schedules.
</div>

## Technical Implementation

**Data Source Integration**: Connected multiple data sources including Zabbix for legacy monitoring, InfluxDB for time-series storage, LibreNMS for Huawei OLT monitoring, and Prometheus for metrics collection. All data sources accessed through Grafana PDC agent using SSH tunneling for secure communication between on-premise infrastructure and Grafana Cloud.

**Dashboard Development**: Built custom Grafana dashboards for network-specific metrics and imported community dashboards for Node Exporter (ID: 1860) and Windows Exporter (ID: 2129). Dashboards provide visualization of interface statistics, optical transceiver temperatures, SFP power levels, CPU/memory utilization, and network traffic patterns with configurable time ranges and drill-down capabilities.

**Network Device Configuration**: Configured Mikrotik routers to forward syslog events to Promtail via port 514 for log collection. Set up Huawei NE40 routers with info-center configuration directing logs to centralized syslog server. Implemented SNMP exporter with relabeling configurations for dynamic target discovery and metric enrichment.

## Deployment and Operations

**Service Management**: Deployed all monitoring components as systemd services on Linux with automatic restart policies and dedicated service accounts. Services include Prometheus (port 9090), Node Exporter (port 9100), Loki (port 3100), Promtail (port 9080), and SNMP Exporter (port 9116) with proper file permissions and resource limits.

**Documentation and Knowledge Transfer**: Created comprehensive 22-page technical documentation covering installation procedures, configuration files, service management commands, data source setup, dashboard creation, and alerting configuration. Documentation includes step-by-step guides for adding new monitoring targets and troubleshooting common issues.

## Results and Impact

Successfully deployed enterprise monitoring solution providing unified visibility across multi-vendor network infrastructure. The platform enables proactive incident detection through automated alerting, reduces mean time to resolution through centralized log analysis, and provides historical trending data for capacity planning and performance optimization. Alert rules continuously monitor critical infrastructure with sub-minute evaluation intervals, ensuring rapid response to network events.

## Technologies Used

`Prometheus` `Grafana` `Grafana Cloud` `Loki` `Promtail` `Node Exporter` `SNMP Exporter` `Windows Exporter` `InfluxDB` `Zabbix` `LibreNMS` `Rsyslog` `Systemd` `Linux` `Grafana OnCall` `Telegram API` `Grafana PDC` `SSH Tunneling` `YAML` `Syslog`