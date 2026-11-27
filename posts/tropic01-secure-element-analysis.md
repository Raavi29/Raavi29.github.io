# Testing a secure element against its datasheet: TROPIC01

## The question

TROPIC01 is a secure element from Tropic Square. It stores cryptographic keys and runs cryptographic operations while resisting key extraction, even with physical access. It has a RISC-V application core, a coprocessor called SPECT for ECC (Ed25519, X25519 and P-256), a hardware TRNG, AES-256-GCM, SHA-256, HMAC, on-chip key storage and a Mac-and-Destroy PIN mechanism. The datasheet states what the chip protects. I tested those statements against the hardware.

The work started in June 2026 at the de.ci.phe.red Lab, IIT Bhilai, under Dr. Dhiman Saha, on the lab's TROPIC01 USB devkit (an STM32U535 bridge sits between the USB port and the chip).

## What I did

- **Passive reconnaissance.** I read the USB descriptor and the device's reported versions.
- **Active exploration and conformance testing.** I sent commands over the bridge and compared the chip's behaviour with the specification.
- **Mac-and-Destroy.** I ran the full lifecycle on hardware: a master secret from the TRNG, then 11 wrong PIN attempts, each destroying one NVM slot.
- **Source and firmware review.** I read the public source and decompiled five functions of the STM32 firmware in Ghidra.
- **Timing.** I checked what software timing can show. It is too coarse for side-channel work, which is why the hardware phase needs a ChipWhisperer.
- **Conformance test suite.** I built one and delivered it to the lab.

The software phase produced 62 findings, each logged against a piece of evidence.

## Where it stands

As of my report of 27 June 2026, the software analysis is complete. The hardware phase has not started: power analysis and SPI bus analysis are still ahead. A ChipWhisperer Husky and a PhyWhisperer USB are in the lab for it.

## What I do not publish

The code and the report belong to the lab, so there is no public repository and no finding-level detail here.
