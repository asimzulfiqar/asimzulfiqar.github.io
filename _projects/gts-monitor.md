---
layout: page
title: GTS Monitor – IoT Platform for Precision Beekeeping
description: A Django-based IoT monitoring platform that calculates Growing Temperature Sum (GTS) using LoRaWAN sensors, weather APIs, and phenology data to predict plant flowering times for optimal beekeeping decisions.
img: assets/img/gts-monitor-dashboard.png
importance: 1
category: work
related_publications: false
---

GTS Monitor is a comprehensive IoT platform designed to support precision beekeeping through temperature monitoring and phenological predictions. The system calculates Growing Temperature Sum (GTS), a critical agrometeorological metric that accumulates daily temperature values above a base threshold to predict plant development stages and flowering times.

## What is GTS and Why It Matters

Growing Temperature Sum (GTS), also known as degree days, is calculated by summing the daily average temperatures above a base threshold (typically 0°C or 5°C) over time. This metric is essential for:

- **Predicting plant phenology**: Different plants require specific GTS thresholds to reach flowering stages
- **Beekeeping optimization**: Knowing when specific plants will bloom helps beekeepers plan hive placement and honey production
- **Agricultural planning**: Understanding thermal time accumulation aids in crop management decisions

The platform uses seasonal weighting to account for varying day lengths and solar intensity throughout the year, providing more accurate predictions than simple temperature accumulation.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/gts-monitor-dashboard.png" title="GTS Monitor Dashboard" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Main dashboard showing real-time GTS calculations, multi-year comparisons, and location maps for deployed sensors.
</div>

## Platform Architecture

The system integrates multiple data sources to provide comprehensive environmental monitoring:

- **LoRaWAN sensor network**: Deployed temperature sensors transmit data via LoRaWAN gateways to Akenza IoT platform
- **Akenza API integration**: Automated data ingestion with device-type-specific field mapping and temperature conversion
- **OpenWeather API**: Provides 7-day forecast data for predictive GTS calculations
- **Open-Meteo API**: Historical weather data as fallback when sensor data is unavailable

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/gts-monitor-settings.png" title="Settings and Plant Management" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/gts-monitor-comparison.png" title="Multi-year GTS Comparison" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: Location update and manual GTS entry interface with plant-based predictions. Right: Historical GTS comparison across multiple years showing seasonal variations.
</div>

## Core Features Implemented

### User & Access Management
- Email verification-based registration system
- Password reset functionality
- Role-based access control
- Rate-limited signup to prevent abuse

### Device & Sensor Management
- Device type registry with customizable field mappings
- Sensor assignment to users
- Interactive location updates using Leaflet maps
- Real-time sensor status monitoring

### GTS Calculation Engine
The platform implements a priority-based data system:
1. **Manual entries** (highest priority) - User-verified corrections
2. **Plant-based entries** - GTS values derived from known phenological events
3. **API sensor data** - Real-time LoRaWAN sensor readings
4. **Forecast data** - OpenWeather predictions for future dates
5. **Historical estimates** - Open-Meteo data when gaps exist

### Plant Phenology Database
- Comprehensive plant library with 40+ species
- GTS thresholds for specific flowering stages
- User-selectable plants per sensor for bloom predictions
- Examples: Snowdrops (35°Cd), Apple pre-bloom (530°Cd), Cherry full bloom (345°Cd)

### Visualization & Analytics
- Interactive Chart.js graphs for GTS and temperature trends
- Multi-year comparison (up to 10 years)
- Year-over-year performance analysis
- Expected flowering plant predictions based on forecast GTS
- Leaflet maps showing sensor locations

## Technical Implementation

**Backend Framework**: Django 5.2 with SQLite database

**Key Technologies**:
- Django REST Framework for API endpoints
- Django Import-Export for data management
- Requests library for external API integration
- Custom middleware for session management

**Frontend Stack**:
- Tailwind CSS for responsive design
- Chart.js for data visualization
- Leaflet.js for interactive maps

**Deployment**:
- UpCloud VPS hosting
- Gunicorn WSGI server
- Production-ready configuration with rate limiting and API throttling

## Data Integrity & Reliability

The platform ensures data accuracy through:
- Conflict resolution rules preventing duplicate entries
- Automated daily data refresh with error handling
- Manual override capabilities for data correction
- Historical data backfilling for continuity
- Temperature unit conversion (Kelvin to Celsius) as needed

## Impact on Beekeeping Operations

By providing accurate GTS tracking and flowering predictions, the platform enables beekeepers to:
- Optimize hive placement based on predicted nectar flows
- Plan colony splits and queen rearing around bloom periods
- Anticipate honey production windows
- Make data-driven decisions rather than relying solely on observation

The multi-year comparison feature helps identify climate trends and adjust management strategies based on historical patterns.

---

**Technologies**: `Django`, `Python`, `SQLite`, `Akenza API`, `OpenWeather API, Open-Meteo API`, `LoRaWAN`, `Chart.js`, `Leaflet.js`, `Tailwind CSS`, `Gunicorn`

**Deployment**: UpCloud VPS

**Role**: End-to-end development including backend logic, API integrations, frontend implementation, database design, and production deployment