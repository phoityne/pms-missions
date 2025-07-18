# Telnet Protocol: Control Code Specification

This document outlines the basic Telnet control sequences used for command negotiation between a Telnet client and server, based on [RFC 854](https://datatracker.ietf.org/doc/html/rfc854).

---

## Control Bytes

| Name  | Hex   | Decimal | Description                                 |
|-------|-------|---------|---------------------------------------------|
| IAC   | 0xFF  | 255     | Interpret As Command prefix                 |
| DO    | 0xFD  | 253     | Request the other party to enable an option |
| DONT  | 0xFE  | 254     | Request the other party to disable an option|
| WILL  | 0xFB  | 251     | Announce willingness to enable an option    |
| WONT  | 0xFC  | 252     | Announce refusal to enable an option        |

---

## Command Format

All Telnet control commands begin with the `IAC` (0xFF) byte, followed by the command type and, if applicable, an option code.

---

## Common Option Codes

| Code | Meaning             |
|------|---------------------|
| 0    | Binary Transmission |
| 1    | Echo                |
| 3    | Suppress Go Ahead   |
| 24   | Terminal Type       |

---

## Notes

- Negotiation is bidirectional: either side may initiate it.
- Unsupported options should be rejected using `WONT` or `DONT`.
- Data bytes containing 0xFF must be escaped by duplication (`IAC IAC`).
