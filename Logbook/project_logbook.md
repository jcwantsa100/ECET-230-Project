# Project Logbook – Personal Weather Station

## Phase: Environmental Sensor Development

### Initial Objective
Integrate environmental sensors with Raspberry Pi to monitor:
- Temperature
- Humidity
- Atmospheric Pressure

The original plan was to use the BME280 for all three measurements.

---

## Hardware Testing – BME280

### Issue Observed
The BME280 modules received were unreliable.

Symptoms:
- Incorrect pin labels
- Inconsistent readings
- Communication failures
- Unstable I2C behavior
- Random read errors

Multiple wiring configurations and library implementations were tested. Stable operation could not be achieved.

### Engineering Decision
Pause BME280 integration and prioritize system stability.

Shift focus to DHT22 for temperature and humidity monitoring to ensure a working subsystem before expanding.

---

## DHT22 Integration

### Hardware Configuration
- DATA → GPIO4 (Physical Pin 7)
- Power → 3.3V
- Ground → Physical Pin 6
- Breakout board includes internal pull-up resistor

Verified correct 3.3V logic compatibility.

---

## Initial Software Implementation

### Version 1 – Basic Read Script
Issue:
- Frequent "DHT sensor not found" errors.

Cause:
- DHT22 uses a timing-sensitive single-wire protocol.
- Linux is not a real-time operating system.
- Timing jitter caused handshake failures.

---

## Stabilization Process

### Version 2 – Retry Logic
Implemented:
- 3 read attempts per sampling cycle
- Short delay between retries
- Storage of last valid reading

Result:
- Significant reduction in visible failures.

---

### Version 3 – Stable Console Monitor
Implemented:
- 2-second sampling interval
- Structured error handling using try/except
- Clean formatted output

Result:
- Reliable temperature and humidity monitoring.

---

### Version 4 – GUI Integration
Integrated sensor into Tkinter interface.

Enhancements:
- Scheduled updates using after()
- Preserved last valid reading during failure
- Added status indicator

Result:
- Stable graphical display without crashes.

---

## Current System Status

Temperature and humidity monitoring are stable.

Subsystem is validated for:
- 2-second sampling
- Retry-based stability
- GUI and console operation

---

## Pending Work

- Reattempt BME280 integration
- Debug I2C instability
- Implement pressure monitoring
- Develop pressure trend detection algorithm
- Integrate rain likelihood notification logic

---

## Key Lessons Learned

- Timing-sensitive protocols require retry strategies under Linux.
- Hardware reliability must be verified early.
- Subsystems should be validated individually before integration.
- Stability is prioritized over feature expansion.

---

## Next Iteration Plan

1. Retest BME280 with controlled wiring and I2C scan verification.
2. Confirm stable pressure readings.
3. Merge DHT22 and BME280 into unified environmental module.
4. Implement pressure trend detection logic.
5. Test alert triggering mechanism.
