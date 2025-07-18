# 🔌 Serial Connection Specifications

These are standard settings commonly used when establishing a serial connection to network devices such as Fortinet appliances.

---

## 📟 Typical Serial Parameters

- **Baud Rate**: `9600` (default), or `115200` on some devices  
- **Data Bits**: `8`  
- **Parity**: `None`  
- **Stop Bits**: `1`  
- **Flow Control**: `None` (No hardware/software flow control)  
- **Encoding**: ASCII / UTF-8  
- **Connector Type**: RJ45 to DB9 or USB-to-Serial adapter  
- **Login Prompt**: Appears after pressing `Enter`  

---

## 🧭 Notes

- Baud rate may vary by device model; always confirm with the hardware manual.
- Make sure no other application is using the same serial port.
- If garbage characters appear, try adjusting baud rate.
- Always close the serial session (`serial-close`) after use.
