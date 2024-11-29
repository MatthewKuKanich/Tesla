# Ambient Lighting Control - 2024 Highland

The ambient lighting control for the 2024 Highland is on the vehicle bus. Below are the details discovered through reverse engineering.

## CAN ID: `0x679`
- **Byte 0 (Mode)**:  
  - Value `0`: Off  
  - Value `2`: On  
  - Value `3`: Setup mode (e.g., when the color picker in the UI is active)

- **Bytes 1, 2, 3**: RGB values (range: `0x00` to `0xFF`)  
  - Byte 1: Red  
  - Byte 2: Green  
  - Byte 3: Blue  

- **Byte 4 (Brightness)**: Brightness level (range: `0x00` to `0xFF`)

- **Byte 5 (Fade Interval)**: Appears to control the fade interval (still under testing).

### Notes:
- **DLC**: 6 bytes  
  - Sending data for bytes 6 or 7 causes the car to ignore the frame.  

- The car sends the ambient lighting frame at a **2 Hz interval**, but it also sends a new frame instantly whenever you change the color or brightness in the UI.

---