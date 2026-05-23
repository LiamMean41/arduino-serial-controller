# Arduino Serial Controller

A Windows desktop application for controlling an Arduino over a serial connection, built in C# with WinForms. Created as a hands-on introduction to serial communication between a PC and a microcontroller.

## Features

- **Relay control** — turn a relay on or off with dedicated buttons
- **Buzzer trigger** — fire a buzzer connected to the Arduino
- **LED brightness** — set a red LED's brightness (0–255) via a slider and send it on demand
- **Button counter** — displays a running count of button presses received from the Arduino over serial

## How it works

The app opens a serial connection to the Arduino on startup and communicates using single-character commands:

| Command sent | Action |
|---|---|
| `R` | Relay on |
| `r` | Relay off |
| `b` | Buzzer trigger |
| `L{0-255}` | Set LED brightness |

Incoming serial data is read line by line. A line beginning with `p` increments the button press counter displayed in the UI.

## Requirements

- Windows (WinForms app)
- .NET Framework 4.x
- Arduino connected via USB serial on **COM5** (change `serialPort1.PortName` in the designer if your port differs)
- Visual Studio or SharpDevelop to build

## Getting started

1. Clone the repo
2. Open `AdruinoGUI/AdruinoGUI.sln` in Visual Studio or SharpDevelop
3. Update the COM port in `MainForm.Designer.cs` if needed
4. Build and run — the app will attempt to open the serial port on launch

## Notes

The COM port is hardcoded to `COM5`. If your Arduino appears on a different port, update `this.serialPort1.PortName` in `MainForm.Designer.cs` before building.
