# Personal Weather Station – ECET 230

## Overview

This project is a Raspberry Pi-based personal weather station designed to monitor environmental conditions in real time.

The system collects temperature, humidity, and (future) pressure data to provide weather-related insights such as rain likelihood detection.

This repository contains development documentation, design decisions, logbook entries, and implementation code.

---

## Current System Status

### Implemented
- DHT22 (AM2302) temperature and humidity sensor
- 2-second stable sampling interval
- Structured retry logic for sensor stability
- Console monitoring version
- Tkinter GUI implementation
- Last-valid-reading preservation for stability

### In Progress
- BME280 pressure sensor integration
- Stable I2C communication validation
- Pressure trend analysis
- Rain likelihood detection logic

---

## Hardware Used

- Raspberry Pi 4
- DHT22 (AM2302)
- Breadboard and jumper wires
- BME280 (integration in progress)

---

## Software Features

- GPIO-based digital sensor interfacing
- Timing-sensitive protocol handling
- Retry logic for improved reliability
- Real-time GUI updates using Tkinter
- Linux hardware permission management

---

## Project Structure

- Design Decisions
- Logbook
- Tasks
- Project Definition
- Source Code

---

## Development Notes

The DHT22 subsystem is fully functional and stable.

The BME280 modules initially received were unreliable. Integration is ongoing to achieve stable pressure readings before implementing pressure-based rain detection logic.
