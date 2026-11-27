# RansomGuard: ransomware detection that preserves evidence

## The idea

Most ransomware detectors stop at an alert. RansomGuard collects evidence at the same moment. When it fires, for example on a spike in file entropy or a process deleting shadow copies, it takes a snapshot of the affected files, the process tree and the network state, and writes them into a timestamped evidence chain.

## Constraints I set

- It runs only against synthetic ransomware-like behaviour in a sandbox. No live ransomware.
- Evidence is stored outside the monitored directory, so the ransomware cannot encrypt it.

## Stack

Python, watchdog, psutil, NumPy, scikit-learn, hashlib, SQLite, Streamlit and pytest, with VirtualBox for the sandbox.

## Where it stands

It is a solo project in the architecture phase, with the prototype in early development. It has no benchmark results yet, so it makes no accuracy claim. I submitted the proposal to UofT ProjectX and it was not selected. I plan to write it up as a paper. The repository is private.
