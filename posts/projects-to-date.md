# Projects to date

The projects I have worked on since I started my B.Tech in August 2025, with dates, what each one is and what state it is in. Where a project is under a lab or industry restriction, I say so and publish no technical detail.

## Security research

### TROPIC01 secure element analysis (June 2026 onwards, in progress)

An independent analysis of Tropic Square's TROPIC01 development kit at the de.ci.phe.red Lab, IIT Bhilai, under Dr. Dhiman Saha. The datasheet makes claims about what the chip protects, and this project tests them against the hardware. The work covers reconnaissance of the USB descriptors, the SPI protocol tested against the conformance spec, the STM32 firmware decompiled in Ghidra, and the Mac-and-Destroy PIN lockout checked across 11 wrong PINs. The work produced 62 findings and a conformance test suite that I delivered to the lab. The code and the report are lab-restricted, so there is no public repository.

### TrusToken (June to August 2026, private)

A cryptographic USB token built by C-DAC Noida and IIT Bhilai. This is an industry project and the report stays inside the lab. I replicated attacks from an earlier B.Tech thesis on the token and documented new attack vectors and observations. I publish no findings or methods here.

### ChipWhisperer Nano (2026, during the IIT Bhilai internship)

Power-trace exploration on a ChipWhisperer Nano, in Jupyter notebooks, to understand how power traces look. I did not capture power traces on TROPIC01.

### Rowhammer in a simulated environment

A Rowhammer attack implemented in a simulated environment.

### Ransomware detection review (accepted and presented at IJCACI 2026, July 2026)

A systematic review of machine learning and deep learning ransomware detection, written with Prof. Merry KP. I am first author. I screened 87 papers, kept 14 studies, and mapped their detection techniques to MITRE ATT&CK phases. The review found a gap between detection accuracy and forensic recoverability. The publishing contract is signed and the paper is not in print yet.

### RansomGuard (architecture phase)

A ransomware detector that collects forensic evidence when it fires. A spike in file entropy or a process deleting shadow copies triggers a snapshot of the affected files, the process tree and the network state, with a timestamped evidence chain. It is built on Python, watchdog, psutil, scikit-learn, SQLite and Streamlit. It runs only against synthetic ransomware-like behaviour in a sandbox and has no benchmark results yet. The repository is private.

### Malware analysis lab (built by October 2026)

A REMnux and FlareVM lab on Host-Only networking, running on my own desktop in a dual-boot Ubuntu and Windows 11 setup.

## Software and open source

### Network intrusion detection system (November 2026)

A Python IDS that groups packets into flows and scores each flow with an Isolation Forest. It is a solo project that I fixed and extended in November 2026. On synthetic traffic it caught three of four attack types. On 2.3 million real CIC-IDS2017 flows it caught none of the DoS Hulk or DDoS traffic. The full result is in [the field note on the real-data test](https://raavi29.github.io/post.html?p=nids-isolation-forest-real-traffic). Code: [Raavi29/Network-Intrusion-Detection-System](https://github.com/Raavi29/Network-Intrusion-Detection-System).

### OWASP Nettacker (merged 15 April 2026)

One merged pull request, #1487, with pytest tests for the FTP and FTPS brute-force libraries. I applied to GSoC 2026, was not selected, and still contribute.

### This site (November 2026)

A static portfolio on GitHub Pages with a Markdown field-notes section. Code: [Raavi29/Raavi29.github.io](https://github.com/Raavi29/Raavi29.github.io).

### File upload and download app (November 2025)

A small Express app that stores uploads in SQLite and returns a unique ID for download, using Multer and UUIDs. Code: [Raavi29/aoop](https://github.com/Raavi29/aoop).

## Competition teams

### Green Light, Smart India Hackathon 2025 (repositories dated November 2025 and March 2026)

Adaptive traffic-signal control as Team Void Pointers from DBS Global University, a national finalist at IIIT Dharwad, where I was the primary presenter. The first prototype, from November 2025, counts vehicles in a lane region with YOLOv8n and applies a simple rule: more than 10 vehicles extends the green phase by 5 seconds, up to a 30 second cap. The hardware output is a stub. The March 2026 version of the repository documents a FastAPI backend with vision, prediction and optimisation endpoints and holds the React and Vite dashboard. We tested the idea with SUMO simulations on Linux. Code: [Raavi29/Green_Light_Team_Void_Pointers](https://github.com/Raavi29/Green_Light_Team_Void_Pointers) and [Raavi29/Void-Pointers](https://github.com/Raavi29/Void-Pointers).

### One True Friend, SAP Hackfest North Region 2026 (August 2026)

An inclusive workforce intelligence platform that reached the finale round. I led the team. The repository is private.

### Saheli, CII Yi Yuva National Grand Finale 2026

A WhatsApp-first labour marketplace for homebound women to take contracts from small businesses, with trust scores, UPI payouts and Hindi voice input. I led the team.
