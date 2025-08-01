# SNES-12MB-Cartridge-with-FRAM-No-Battery-Save-

# SNES 12MB Cartridge with FRAM (No Battery Save)

This project is a custom Super Nintendo (SNES) cartridge design featuring up to **12MB of ROM** and **non-volatile FRAM** for save data, eliminating the need for a battery.

## 🧩 Features

- 🧠 **Up to 12MB of ROM** using three 4MB Flash chips (U1, U2, U3)
- 💾 **FRAM (FM1608)** for game save data (no battery required)
- ⚙️ **Address decoding** using 74LS139 logic ICs
- 🔀 **ROM chip selection** based on A21 and A22 address lines
- 🔧 **FRAM control logic** (CE, OE, WE) generated using 7400 NAND gates
- 🔌 **SNES-compatible edge connector (CART-EXP)**
- 🔐 **CIC clone** for lockout chip bypass (region protection)
- ⚡ **3.3V regulator (LM1117)** to power modern Flash memory

## 🛠️ How It Works

- The **ROM data** is split across 3 chips. A 74LS139 decoder selects which chip is active using address lines A21 and A22. ( Very hard to decode😩)
- The **FM1608 FRAM** acts as the SRAM replacement. It stores game saves even after power is off.
- A second 74LS139 generates the **CE-RAM** signal based on address lines A13–A15.
- A set of **7400 NAND gates** combines `CE`, `OE`, and `WE` to produce the correct control signals for the FRAM: `CE-FRAM`, `OE-FRAM`, and `WE-FRAM`.
- A **CIC clone** chip ensures compatibility with the original SNES hardware.

## 🧾 Components

| Component | Function |
|----------|----------|
| U1–U3 | Flash ROM (up to 4MB each) |
| U4 | FM1608 FRAM (32KB, batteryless save) |
| IC1A, IC1B | 74LS139 Decoders (address decoding) |
| U5 | 7400 Quad NAND gate (FRAM control logic) |
| U6 | LM1117 3.3V regulator |
| U9 | CIC Clone (lockout bypass) |
| Cx | Decoupling capacitors |

## 📐 Schematic Overview

<img width="2643" height="1105" alt="Schematic" src="https://github.com/user-attachments/assets/22e5431c-e28b-4bb3-9047-3018d34d7c33" />

Top PCB Layer

<img width="808" height="607" alt="Top" src="https://github.com/user-attachments/assets/647d7708-3e9e-4b59-91fd-4fde708d1326" />

Bottom PCB Layer

<img width="815" height="620" alt="Bottom" src="https://github.com/user-attachments/assets/07f18437-7cfd-4433-91ad-eb89c8db6245" />

The design supports both LoROM and HiROM game types, depending on how the ROM is split and addressed. The control logic is fully discrete and compatible with original SNES hardware.

> **Note:** You must flash the ROMs properly and map the game correctly to match your decoder logic (A21/A22 addressing).

## 🧪 Usage

- Insert the cartridge into a SNES console.
- Game will load from ROM (up to 12MB supported).
- Save data is automatically stored in FRAM — no battery needed!

## 🧰 Tools Used

- 🖥️ Schematic Design: [EAGLE CAD](https://www.autodesk.com/products/eagle/)
- 🔄 Simulation & Testing: oscilloscope for logic analyzer

## 📎 Files Included

- `Schematic.png` – Circuit diagram
- `Gerber/` – PCB manufacturing files (optional)
- `README.md` – This documentation

## 📦 Future Improvements

- Add support for 29F032 chips (32-bit)
- Integrate SuperCIC for region-free behavior
- Implement onboard ROM flashing via USB (dev version)

## 📜 License

This project is open-source. Feel free to use, modify, and distribute under the MIT License.
Do not copy this project to sell.

---

Created with ❤️ for the SNES development and repro community. 
