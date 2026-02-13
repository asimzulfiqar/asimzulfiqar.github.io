---
layout: page
title: Hotel Room Automation System – Smart IoT Control Platform
description: A Raspberry Pi-based IoT platform for hotel room automation managing 50+ rooms with centralized monitoring, control dashboards, and real-time data visualization for lights, HVAC, curtains, and environmental sensors.
img: assets/img/hotel-room-control.png
importance: 2
category: work
related_publications: false
---

A comprehensive IoT automation system designed for hotel room management, enabling centralized control and monitoring of room devices including lighting, HVAC, curtains, motion sensors, and power outlets through an intuitive web-based dashboard.

## System Overview

The platform provides hotel staff with real-time visibility into room status across the entire property, including occupancy detection, environmental conditions, and device states. Each room features individual control panels while maintaining centralized oversight through a unified dashboard interface.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/hotel-dashboard-table.png" title="Centralized Hotel Dashboard" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Centralized dashboard providing at-a-glance status of all rooms including keycard status, presence detection, device states, and environmental conditions.
</div>

## Architecture

Built on Raspberry Pi as the central gateway, the system coordinates communication between Room Control Units (RCUs) and the monitoring infrastructure using MQTT protocol for reliable real-time messaging.

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/hotel-architecture.png" title="System Architecture" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/hotel-grafana.png" title="Performance Monitoring" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: System architecture showing MQTT broker, Node-RED flow engine, and InfluxDB time-series storage. Right: Grafana dashboard monitoring Raspberry Pi performance metrics.
</div>

## Core Components

**EMQX MQTT Broker**: Handles message routing between 50+ RCUs and the central system with publish/subscribe architecture for scalable communication.

**Node-RED Flow Engine**: Implements business logic for device control, processes sensor data, and generates the responsive dashboard interface with real-time updates.

**InfluxDB Time-Series Database**: Stores historical device states and environmental data for analytics, trend analysis, and reporting.

**Prometheus & Grafana**: Monitor system health including CPU usage, memory consumption, network traffic, and service availability.

## Room Control Features

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/hotel-room-control.png" title="Individual Room Dashboard" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/hotel-multi-room.png" title="Multi-Room Overview" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: Individual room control interface with device status indicators and controls. Right: Multi-room overview showing simultaneous monitoring of multiple guest rooms.
</div>

Each room provides control and monitoring for:

- **Lighting Systems**: Individual light control with dimming capabilities (0-100%)
- **HVAC Management**: Temperature setpoint control, mode selection (cooling/heating/fan), fan speed adjustment, real-time temperature display
- **Curtain Control**: Open, close, and stop commands for motorized window treatments
- **Access Control**: Keycard insertion detection and room access status
- **Occupancy Detection**: Motion sensors and presence indicators for room occupancy
- **Entertainment**: Music system controls and TV power management
- **Power Management**: Individual outlet control for energy optimization

## Technical Implementation

**Communication Protocol**: MQTT topics structured as `<rtu_path>/P` for status publishing and `<rtu_path>/S` for control commands, enabling bi-directional communication with each RCU.

**Data Storage**: Python MQTT client subscribes to device topics and writes time-stamped measurements to InfluxDB for historical tracking and analysis.

**Dashboard Generation**: Node-RED dashboard nodes create responsive web interface accessible at `http://<RPI_IP>:1880/ui` with no additional frontend development required.

**Scalability**: Automated replication script generates Node-RED flows for multiple rooms from CSV configuration, enabling rapid deployment across 50+ rooms.

## Automation & Deployment

**Flow Replication**: Python script reads room configuration from CSV and generates complete Node-RED flows with unique IDs, MQTT topics, and dashboard tabs for each room automatically.

**System Backup**: Complete SD card imaging procedures using Win32 Disk Imager for disaster recovery and rapid replication to additional Raspberry Pi units.

**Infrastructure as Code**: Ansible playbooks automate installation of EMQX, Node-RED, InfluxDB, Prometheus, and Grafana, ensuring consistent deployments and simplified maintenance.

**Testing Framework**: Simulated 50 virtual devices with 10 parameters each to validate system performance, message throughput, and database write capacity before production deployment.

## Service Management

All services configured as systemd units for automatic startup on boot:
- EMQX broker accessible at port 1883 (MQTT) and 18083 (web UI)
- Node-RED running on port 1880
- InfluxDB on port 8086
- Grafana visualization on port 3000
- Prometheus metrics collection on port 9090

System monitoring through Node Exporter provides hardware metrics to Prometheus, visualized in Grafana dashboards tracking CPU utilization, memory usage, disk I/O, and network bandwidth.

## Benefits

- **Centralized Management**: Single interface for monitoring and controlling all hotel rooms
- **Energy Efficiency**: Presence-based automation and power management reduce energy consumption
- **Guest Comfort**: Fine-grained environmental controls and responsive HVAC systems
- **Operational Insights**: Historical data enables occupancy analysis and predictive maintenance
- **Scalability**: Architecture supports expansion from 50 to 200+ rooms without redesign

---

**Technologies**: Raspberry Pi, Node-RED, EMQX MQTT, InfluxDB, Python, Grafana, Prometheus, MQTT Protocol, Ansible

**Deployment**: Raspberry Pi 4 with systemd service management

**Role**: End-to-end system design, MQTT architecture, Node-RED flow development, Python data pipeline, automation scripting, infrastructure deployment