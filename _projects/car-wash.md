---
layout: page
title: Industrial Car Wash Automation System
description: A Controllino PLC-based automated car wash control system with integrated payment terminal, multi-state operation, visual feedback, and receipt printing capabilities for commercial vehicle washing operations.
img: assets/img/car-wash-system.png
importance: 1
category: work
related_publications: false
---

An industrial automation solution for commercial car wash operations, integrating payment processing, state machine control logic, sensor monitoring, and customer feedback systems through a Controllino MAXI PLC platform running custom Arduino firmware.

## System Overview

The system controls a complete car wash operation cycle with integrated payment validation, multi-stage washing sequences, real-time sensor monitoring, and automated receipt generation. The controller manages all aspects of operation from payment acceptance through wash cycle completion with comprehensive visual feedback through LED indicators.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/car-wash-system.png" title="Car Wash Control System" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Industrial car wash automation system with Controllino PLC controlling payment integration, sensor monitoring, and wash cycle progression with visual LED feedback.
</div>

## Control Architecture

**State Machine Implementation**: Designed finite state machine with five distinct operational states including standby, payment verification, pressure detection, flow monitoring, and completion. Each state transition is triggered by specific sensor inputs or timeout conditions, ensuring safe and predictable operation sequences.

**Payment Terminal Integration**: Implemented relay-based communication protocol with third-party payment terminal supporting multiple payment tiers. System detects payment completion pulses and unlocks operation accordingly, with automatic timeout and reset functionality to prevent unauthorized usage.

**Sensor Fusion and Debouncing**: Integrated pressure switch and flow sensor inputs with 1-second software debounce filters to eliminate false triggers from electrical noise and mechanical vibrations. Real-time sensor state monitoring enables adaptive control logic based on actual operating conditions.

## User Interface and Feedback

**NeoPixel LED Progression**: Programmed dual 30-LED RGB strips providing real-time visual feedback of wash cycle progress. Implemented non-blocking LED animation routines including progressive illumination, flashing patterns, and color-coded state indication with separate timing control for different operational modes.

**Button Interface**: Dual push-button control with integrated LED indicators for start/stop operations. Implemented non-blocking debounce logic and state-aware button handling to prevent accidental activation during active wash cycles.

**Thermal Receipt Printer**: Configured RS232 serial communication with VKP80II thermal printer using ESC/POS command protocol. Developed custom print formatting functions supporting variable receipt templates based on payment tier, timestamp generation from onboard RTC, and automatic paper feed and cut commands.

## Hardware Integration

**Controllino MAXI PLC**: Utilized industrial-grade Arduino-compatible PLC with 24V I/O, real-time clock, multiple communication interfaces, and DIN-rail mountable housing. Configured analog and digital inputs for sensor monitoring, relay outputs for actuator control, and software serial for printer communication.

**Relay Control Logic**: Implemented output control for pressure washer activation, payment terminal enable/disable, and counter pulse generation. Designed interlock logic preventing simultaneous conflicting operations and ensuring safe shutdown sequences.

**Real-Time Clock Integration**: Configured Controllino RTC module for accurate timestamping of wash cycles and receipt generation. Implemented automatic compile-time initialization with persistent timekeeping across power cycles.

## Firmware Development

**Non-Blocking Architecture**: Developed entirely non-blocking control code using millis()-based timing for all delays, LED animations, and timeout functions. This architecture ensures responsive button handling and smooth LED transitions without code execution blocking.

**Progressive LED Control**: Engineered separate progression tracking for different wash modes with independent timing intervals (12.5 seconds for standard mode, 2.5 seconds for express mode). Implemented automatic LED strip reset and continuation logic maintaining visual feedback across state transitions.

**Error Handling and Recovery**: Built comprehensive timeout mechanisms and emergency stop functionality via red button interrupt. System automatically returns to standby mode after preset inactivity periods or manual abort, with complete state reset and hardware deactivation.

## Results and Deployment

Successfully deployed automated car wash control system providing reliable payment-to-completion operation cycles. The system enables unattended operation with clear visual feedback, automated receipt generation, and fail-safe shutdown mechanisms. Multi-tier payment support allows flexible pricing strategies while maintaining consistent user experience across different service levels.

## Technologies Used

`Arduino` `Controllino MAXI PLC` `C/C++` `State Machine` `Adafruit NeoPixel` `RS232 Serial` `ESC/POS Protocol` `Real-Time Clock` `Relay Control` `Sensor Integration` `Hardware Debouncing` `Non-Blocking Programming` `Industrial Automation` `PLC Programming`