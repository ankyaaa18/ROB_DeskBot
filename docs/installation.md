### Setup : 

- **Arduino IDE** or **PlatformIO**
- **ESP32 Board Package**
- Required **Libraries**:
  - `WiFi` (Built-in with ESP32)
  - `WebServer` (Built-in with ESP32)
  - `Wire` (Built-in)

    Go to **Sketch** -> **Include Library** -> **Manage Libraries** -> **Search and Install** :
   - `Adafruit GFX Library`
   - `Adafruit SSD1306`

### PlatformIO Setup :
```ini
[env:esp32dev]
platform = espressif32
board = esp32dev
framework = arduino

lib_deps =
    adafruit/Adafruit SSD1306
    adafruit/Adafruit GFX Library
```

1. Upload the code using Arduino IDE (Select correct Board and COM Port) or PlatformIO.
2. Connect to WiFi
3. Access Web Interface -> Open browser to *192.168.4.1*
4. Controls :

| Button | Action |
|---------|--------|
| Forward | Move Forward |
| Reverse | Move Backward |
| Left | Turn Left |
| Right | Turn Right |
| Stop | Stop Motors |
| Spin CW | Rotate Clockwise |
| Spin CCW | Rotate Counter Clockwise |
| Explore | Autonomous Movement |
| Blink | Blink Animation |
| Wink | Wink Animation |
