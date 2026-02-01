# Portable Aesthetic Phone

A small portable phone-style device with a touchscreen, multiple sensors, and battery, built on ESP32-S3.

## Description

This compact device is a custom-built phone-style computer featuring an ESP32-S3 microcontroller with a 3.5-inch capacitive touch display. It includes multiple sensors, built-in speakers, camera, and battery headers, all designed to help throughout the day with a modern, aesthetic UI.

The device runs a custom "Phone OS" with LVGL-based UI, featuring a lock screen, home screen, and multiple apps including camera, music player, microphone testing, and gyroscope readings. The interface supports swipe gestures for intuitive navigation.

## Motivation

I wanted to build a small phone with numerous sensors and outputs. By building my own, I have complete control over the UI, apps, and how it functions.

I was inspired by [The Light Phone](https://www.thelightphone.com/), but wanted a full-color high-refresh-rate display instead of e-ink. I aimed for approximately a 3.5-inch display with a super modern and cool look, along with relatively long battery life.

When picking out the parts for this project, I wanted to make sure that anyone who came across this could easily make it even if they had very little experience. So I decided to go with a pre-built module combining everything needed instead of building a custom PCB.

## Hardware Design

### Initial Sketch

Portable-aesthetic-phone/Images
/Sketch.jpg


### Case Design

The case was designed to have enough space for a battery and a little button to press on the buttons on the dev board. It's designed to be printed in a dark blue color that suits the black of the display.

The design started from a smaller case for the same dev board, but was extended to add space for a battery, peripheral holes for the microphone and speaker, and various tweaks. It was printed on an Ender 3 S1 to ensure it's printable without supports.



**Assembly Requirements:**
- 4x M2x8 Countersunk Screws to secure the case

### 3D Models

The CAD folder contains:
- `Case.stl` - Main case body
- `Button.stl` - Button component

## Features

- **Touch Display:** 3.5-inch capacitive touch display with 320x480 resolution
- **LVGL UI:** Modern phone-style interface with swipe gestures
- **Lock Screen:** RTC-based timekeeping with clock display
- **Home Screen:** App launcher with grid layout
- **Music Player:** Play MP3 files from SD card with playback controls
- **Camera App:** Photo capture and video recording capabilities
- **Gyroscope Test:** Real-time gyroscope readings display
- **Microphone Test:** Audio level monitoring and display
- **Control Center:** Volume, brightness, WiFi, and system stats
- **Settings:** WiFi configuration and network scanning
- **Power Management:** Screen timeout, low power mode, and battery monitoring

## Hardware Requirements

| Component | Specification | Notes |
|-----------|---------------|-------|
| Development Board | Waveshare ESP32-S3 3.5 inch Capacitive Touch Display | Main board with all sensors |
| Display | 3.5" 320x480 ST7796 LCD | Built into dev board |
| Touch | FT6X36 Capacitive Touch | Built into dev board |
| Camera | OV2640 | Built into dev board |
| Audio Codec | ES8311 | Built into dev board |
| Power Management | AXP2101 PMU | Built into dev board |
| Battery | 3.7V 2000mAh LiPo (103454) | With JST connector |
| Storage | SD Card | For music and photos |

### Pin Configuration

| Function | Pin |
|----------|-----|
| LCD Backlight | GPIO 6 |
| SPI MISO | GPIO 2 |
| SPI MOSI | GPIO 1 |
| SPI SCLK | GPIO 5 |
| LCD DC | GPIO 3 |
| I2C SDA | GPIO 8 |
| I2C SCL | GPIO 7 |
| Boot Button | GPIO 0 |
| I2S SDOUT | GPIO 16 |
| I2S BCLK | GPIO 13 |
| I2S LRCK | GPIO 15 |
| I2S MCLK | GPIO 12 |
| SD CLK | GPIO 11 |
| SD CMD | GPIO 10 |
| SD D0 | GPIO 9 |

## Software Dependencies

Install these libraries via Arduino IDE Library Manager or PlatformIO:

- **Arduino_GFX_Library** - Graphics library for display
- **lvgl** - Light and Versatile Graphics Library for UI
- **TCA9554** - I/O expander library
- **TouchDrvFT6X36** - Touch driver
- **XPowersLib** - Power management library
- **Audio** - ESP32 audio library
- **es8311** - Audio codec driver
- **WiFi** (built-in)
- **SD_MMC** (built-in)
- **Wire** (built-in)
- **Preferences** (built-in)
- **esp_camera** (built-in)

## Configuration

Before uploading, edit the following in `Firmware/main.ino`:

```cpp
// WiFi Configuration
const char* WIFI_SSID = "YOUR_WIFI_SSID";
const char* WIFI_PASS = "YOUR_WIFI_PASSWORD";

// Time Configuration
#define NTP_SERVER "pool.ntp.org"
#define GMT_OFFSET_SEC 3600
#define DAYLIGHT_OFFSET_SEC 3600
#define SCREEN_TIMEOUT_MS 10000
```

## Usage

### Navigation

- **Swipe Left/Right:** Navigate between screens
- **Tap:** Select items and interact with UI elements
- **Swipe Down from Top:** Open control center

### Lock Screen

The lock screen displays:
- Current time in 12-hour format
- Date
- Battery percentage
- WiFi status
- Now playing music widget (when music is active)

### Home Screen

Grid of app icons for:
- Music Player
- Camera
- Settings
- Gyroscope Test
- Microphone Test

### Music Player

- Browse MP3 files from SD card
- Play/Pause controls
- Volume adjustment
- Song title display

### Camera

- Photo capture mode
- Video recording mode
- Photos/videos saved to SD card

### Control Center

Access system controls:
- Volume slider
- Brightness slider
- WiFi status
- Battery percentage
- IP address
- System stats (CPU, RAM, PSRAM, SD usage, uptime)

## Bill of Materials (BOM)

| Component | Quantity | Price | Link |
|-----------|----------|-------|------|
| Waveshare ESP32-S3 3.5" Touch LCD | 1 | ~$30 | [Waveshare](https://www.waveshare.com/esp32-s3-touch-lcd-3.5.htm) |
| EEMB 3.7V 2000mAh 103454 LiPo Battery | 1 | ~$15 | Search "EEMB 103454 2000mAh" on Amazon |
| M2x8 Countersunk Screws | 4 | ~$5 | Hardware store |
| MicroSD Card | 1 | ~$10 | Various |

## Case

The case STL files are located in the `CAD` folder:
- Print the main case body (`Case.stl`)
- Print the button component (`Button.stl`)

**Print Settings:**
- Material: PLA (dark blue recommended)
- Supports: Not required
- Infill: 20% or higher

## License

MIT License

## About

A portable aesthetic phone device built with ESP32-S3, featuring a touch display, camera, audio, and multiple sensors in a custom 3D-printed case.

## Resources

- [Waveshare ESP32-S3 Touch LCD 3.5 Documentation](https://www.waveshare.com/wiki/ESP32-S3-Touch-LCD-3.5)
- [LVGL Documentation](https://docs.lvgl.io/)
- [Arduino ESP32 Documentation](https://docs.espressif.com/projects/arduino-esp32/)
