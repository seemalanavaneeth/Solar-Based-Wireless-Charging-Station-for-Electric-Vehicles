# Solar-Based Wireless Charging Station for Electric Vehicles
An automated, dual-slot wireless charging station for electric vehicles (EVs) that runs entirely on solar energy. The system detects a vehicle as soon as it parks, wirelessly transfers power to it via inductive coupling, and displays live status updates — all without a single charging cable.

Built as a final-year B.Tech (ECE) project to demonstrate a practical, sustainable, and user-friendly alternative to conventional plug-in EV charging.

---

# Overview

One of the biggest deterrents to EV adoption is charging infrastructure — stations are scarce, cables are inconvenient, and range anxiety is real. This project tackles that problem with a **self-sufficient, contactless charging station** that:

- Runs on **solar power**, cutting dependence on the grid
- Charges vehicles **wirelessly**, removing the need for physical connectors
- Works **automatically** — no manual intervention once a vehicle is parked
- Supports **two vehicles simultaneously**, each charging independently

The concept of wireless power transfer (first introduced by Nikola Tesla) is applied here using resonant inductive coupling between a transmitter coil (charging pad) and a receiver coil (on the vehicle).

---

# How It Works

1. **Sunlight → Energy** — The solar panel converts sunlight into electricity, which is stored in a 12V rechargeable battery.
2. **Vehicle Detection** — When a vehicle parks in a charging slot, an IR sensor detects it and signals the Arduino Nano.
3. **Charging Activation** — The Arduino triggers the corresponding relay, which powers up the transmitter coil for that slot.
4. **Wireless Power Transfer** — The primary coil generates an electromagnetic field; the secondary coil on the vehicle picks it up and converts it back to usable power.
5. **Live Status Updates** — The 16x2 LCD displays real-time messages such as:
   - `Slot Available – Park to Charge`
   - `Vehicle Detected – Charging Started`
   - `Battery Full – Charging Stopped`
6. **Auto Shutoff** — Once charging is complete, the relay disengages to stop power transmission.

Both slots operate independently, so two vehicles can be detected and charged at the same time.

---

# System Architecture

```
                ┌─────────────┐
    Sunlight → │ Solar Panel │
                └──────┬──────┘
                       ▼
                ┌─────────────┐
                │ 12V Battery │
                └──────┬──────┘
                       ▼
   IR Sensors → ┌─────────────┐ → 16x2 LCD (status)
                │ Arduino Nano│
                └──────┬──────┘
              ┌────────┴────────┐
              ▼                 ▼
         ┌─────────┐       ┌─────────┐
         │ Relay 1 │       │ Relay 2 │
         └────┬────┘       └────┬────┘
              ▼                 ▼
       Wireless Coil       Wireless Coil
         (Slot 1)            (Slot 2)
              ▼                 ▼
           EV / Car 1        EV / Car 2
```

---

# Hardware Components

| Component                  | Specification                                  |
|-----------------------------|-------------------------------------------------|
| Microcontroller             | Arduino Nano (ATmega328P, 16 MHz)               |
| Solar Panel                 | 12V, 20W polycrystalline PV module              |
| Battery                     | 12V, rechargeable DC battery                    |
| Vehicle Detection            | IR proximity sensors (x2, one per slot)         |
| Display                     | 16x2 LCD with I2C driver module                 |
| Switching                   | 2-channel relay module                          |
| Power Transfer               | Transmitter (primary) & receiver (secondary) coils — inductive coupling |
| Voltage Regulation           | 7805 (5V) & 7809 (9V) three-terminal regulators |

# Software Used

- **Arduino IDE** — firmware development and upload
- **Embedded C** — microcontroller programming
- **Proteus** — circuit simulation and validation

---

# Key Features

-  Fully solar-powered — no reliance on grid electricity
-  Truly wireless — no cables, no connectors, no wear and tear
-  Automatic vehicle detection and charge activation via IR sensors
-  Real-time status feedback on LCD
-  Dual-slot support with independent, simultaneous operation
-  Overcharge protection via automatic relay shutoff
-  Eco-friendly, low-maintenance, and scalable design

---

# Results

The prototype was built and tested using toy EVs to demonstrate the charging flow end-to-end — vehicle detection, coil activation, wireless power transfer, and LCD status updates for single-slot, dual-slot, and simultaneous charging scenarios.

*(Add your project photos/GIFs here — e.g. `docs/setup.jpg`, `docs/slot1-charging.jpg`, `docs/dual-slot-charging.jpg`)*

---

# Future Scope

- Scale up coil design and power ratings for real EVs (beyond prototype scale)
- Add MPPT-based solar charge controller for higher conversion efficiency
- Integrate IoT (ESP32 + cloud dashboard) for remote monitoring and analytics
- Add RFID/app-based authentication for secure, user-specific charging
- Deploy at public parking lots, residential complexes, and highway rest stops

---

# Team

Developed by final-year ECE students as part of the B.Tech curriculum:

- Ch. Vandana
- K. Amrutha
- S. Navaneeth
- Ch. Abhishek

**Guided by:** Dr. A. Venkateswara Rao, Ph.D, Associate Professor, Dept. of ECE
**Institution:** Miracle Educational Society Group of Institutions (Autonomous), Bhogapuram — Affiliated to JNTU Gurajada Vizianagaram

---

# References

Key references and prior work that informed this project's design are listed in the full project report (`/docs` or project report PDF in this repo).

---

## 📄 License

This project is open for academic and educational use. Feel free to fork, learn from, and build upon it — attribution appreciated.
