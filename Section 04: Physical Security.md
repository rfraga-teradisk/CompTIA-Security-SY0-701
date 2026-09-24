# Physical Security

## Objectives
- Understand physical security controls and their purpose
- Compare preventive, detective, and deterrent physical controls
- Explain how physical security protects systems, people, and data

## Table of Contents

1. [Physical Security](#physical-security)
2. [Physical Security Controls](#physical-security-controls)
3. [Facility Access Controls](#facility-access-controls)
4. [Surveillance and Monitoring](#surveillance-and-monitoring)
5. [Environmental Controls](#environmental-controls)
6. [Device and Media Security](#device-and-media-security)
7. [Physical Attacks](#physical-attacks)
8. [RFID and NFC Attacks](#rfid-and-nfc-attacks)
9. [Key Takeaways](#key-takeaways)

## Physical Security

- **Physical Security:** Controls used to protect people, facilities, systems, equipment, and data from physical threats.
- Cybersecurity is not only digital. If someone can physically access systems, they may bypass technical controls.

Examples:
- Locked server room
- Badge access
- Security camera
- Visitor log
- Cable lock
- Fire suppression

## Physical Security Controls

- **Preventive Controls:** Stop unauthorized physical access.
  - Example: Lock, fence, badge reader.

- **Detective Controls:** Identify or record physical security events.
  - Example: Camera, motion sensor, alarm.

- **Deterrent Controls:** Discourage unwanted behavior.
  - Example: Warning sign, visible camera, security guard.

## Facility Access Controls

Common facility controls:
- Locks
- Badges
- Biometric readers
- Mantraps
- Turnstiles
- Security guards
- Visitor badges
- Visitor logs

- **Mantrap:** Controlled area with two doors where the first door must close before the second opens.
- Helps prevent tailgating.

## Surveillance and Monitoring

- **CCTV:** Camera system used to monitor and record activity.
- **Motion Sensor:** Detects movement in protected areas.
- **Alarm:** Alerts when unauthorized access or unsafe condition occurs.

Surveillance is useful for:
- Deterrence
- Investigation
- Evidence collection
- Real-time monitoring

## Environmental Controls

Environmental controls protect systems from physical damage.

Examples:
- Fire suppression
- Smoke detector
- Temperature control
- Humidity control
- UPS
- Generator
- Water leak detection

## Device and Media Security

Device and media controls include:
- Cable locks
- Locked cabinets
- Secure disposal
- Shredding
- Degaussing
- Drive wiping
- Asset tags
- Clean desk policy

## Physical Attacks

Examples:
- Tailgating
- Shoulder surfing
- Dumpster diving
- Theft of laptop or phone
- Rogue device plugged into network
- USB baiting
- RFID badge cloning

### Physical Brute Force

- Uses physical force or tools to defeat doors, windows, locks, safes, or other barriers; it is distinct from password guessing.
- Barriers delay entry. Resistance depends on construction, installation, tools, and attack duration; safe ratings apply under specified test conditions.
- Combine barriers with detection and a timely response so an intruder cannot work undisturbed.

### Environmental Attacks

- Tampering with power, cooling, humidity controls, or sensors can damage equipment or interrupt operations.
- Network-connected building systems may also provide an entry point into other systems if access and segmentation are weak. Network connectivity alone does not mean a system is easily compromised.
- Restrict management access, segment building-control networks, maintain supported software, monitor changes and sensor readings, and plan for loss of power or cooling.

## RFID and NFC Attacks

- **Radio-Frequency Identification (RFID):** Uses radio communication between a reader and a tag or card to identify an object or credential.
- **Near Field Communication (NFC):** A short-range contactless technology used in applications such as mobile payments and access credentials.
- Common applications include building access badges, transit tickets, contactless payments, inventory tracking, and attendance systems.

| Attack | Meaning |
| --- | --- |
| **Unauthorized Reading / Skimming** | Reads exposed tag or card data without permission. What can be read depends on the technology and its protections. |
| **Eavesdropping** | Captures communication between a legitimate reader and a tag or card. |
| **Cloning** | Copies credential data to another device to impersonate the original. Systems that trust only a static, readable identifier are particularly vulnerable. |
| **Relay Attack** | Forwards communication between a real credential and a distant reader, making the credential appear nearby without necessarily copying its secrets. |

Example: If a door reader accepts a badge solely by its static identifier, an attacker who copies that identifier may gain access using a duplicate badge. Reading an identifier alone does not defeat a system that also requires valid cryptographic authentication. RFID risks and protections depend on the implementation; see [NIST's RFID security guidance](https://csrc.nist.gov/pubs/sp/800/98/final).

### Payment Card Clarification

- Do not assume that every RFID/NFC card exposes all payment details or can be fully cloned with a generic reader.
- EMV chip payments, including contactless payments, use transaction-specific cryptographic protections. Copying readable account details is not equivalent to duplicating the chip's ability to authenticate transactions. See [EMVCo's explanation of chip security](https://www.emvco.com/knowledge-hub/how-do-emv-chip-specifications-tackle-card-fraud/).
- ATM and fuel-pump skimming commonly involves a malicious reader capturing magnetic-stripe data, sometimes accompanied by a camera or keypad overlay to capture a PIN. This is distinct from wireless RFID reading. See the [FBI's skimming guidance](https://www.fbi.gov/how-we-can-help-you/common-frauds-and-scams/skimming).

### Reducing RFID Risk

- Use credentials and readers that support strong cryptographic authentication rather than relying only on a static identifier.
- Require an additional factor, such as a PIN or biometric, for sensitive physical access.
- Revoke lost or stolen badges promptly and review unusual access events.
- Protect readers against tampering and secure their connections to access-control systems.
- Appropriate shielding sleeves can reduce unauthorized reading while cards are enclosed; they do not replace authentication or protect a card during use.

## Key Takeaways

- Physical access can lead to digital compromise.
- Physical security protects systems, users, and data from real-world threats.
- Distinguish RFID reading, cloning, and relay attacks; contactless technology alone does not determine whether a credential can be copied or abused.
