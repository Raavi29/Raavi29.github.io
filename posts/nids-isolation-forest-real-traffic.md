# An Isolation Forest IDS that passes on synthetic traffic and misses DoS on real traffic

## What I built

The IDS groups packets into flows and computes 13 features per flow: packet and byte counts, duration, packet and bit rate, packet length mean and spread, SYN, FIN and ACK ratios, mean inter-arrival time, and TCP/UDP flags. An Isolation Forest scores each finished flow, and a score below -0.05 raises an alert. It reads live capture, replays PCAP files or generates synthetic traffic, and a Streamlit dashboard shows the alerts. The test suite has 27 pytest tests and all pass.

Code: [Raavi29/Network-Intrusion-Detection-System](https://github.com/Raavi29/Network-Intrusion-Detection-System)

One-page summary: [PDF](posts/Parneet_Kaur_NIDS_One_Pager.pdf)

## The synthetic result

On traffic from my own generator, 2 of 1,000 benign flows were flagged. SYN flood, bulk exfiltration and UDP flood were each detected 200 of 200 times. A slow port scan was detected 0 of 200 times.

I wrote both the attacks and the baseline of normal traffic, so this result shows that the pipeline runs from packets to alerts. It does not measure accuracy on real attacks.

## The real-data test

I trained on Monday of CIC-IDS2017, which contains only benign traffic, and tested on the labelled flows of Tuesday to Friday. The 13 features are rebuilt from the dataset's flow statistics, so this tests the model and the feature design, not packet capture. The alert threshold comes from the benign training data only: it is set so that 1% of Monday's training flows alert. Flows with fewer than 5 forward packets are never scored.

- 2,300,825 flows tested, of which 557,646 are attacks. 596,374 flows are long enough to be scored.
- Pooled AUC across the four days is 0.78.
- At the calibrated threshold the detector raised 13,789 false alarms (3.6% of scored benign flows) and detected 48 of 211,137 scored attack flows. Precision is 0.35%.
- DoS Hulk: 0 of 144,430 scored flows detected.
- DDoS: 0 of 46,619 detected, with AUC 0.42.
- FTP-Patator and SSH-Patator: 0 detected, with AUC 0.36 and 0.34.
- PortScan: 158,930 flows, 131 long enough to score, 0 detected.
- Bot: 42 of 118 detected. Infiltration: 6 of 32.

An AUC of 0.78 looks moderate. It does not mean the detector works. The pooled figure hides a per-day range from 0.35 on Tuesday to 0.87 on the Thursday infiltration day, and at any threshold with a usable false alarm rate the detector catches almost none of the attacks.

## Why it fails

An Isolation Forest scores a flow by how quickly it can be separated from the rest. Rare, odd flows separate quickly. A DoS or brute-force attack produces a very large number of near-identical flows, and a dense group of similar points is hard to separate, so it scores as normal. An AUC below 0.5 for DDoS, FTP-Patator and SSH-Patator fits this: those attack flows look more normal to the model than the benign flows do. I have not tested this explanation directly.

Training on the same day's benign flows removes the shift between Monday and the later days but does not fix the result. AUC stays between 0.30 and 0.84 depending on the day.

The features themselves carry signal. A supervised random forest on the same 13 features reaches AUC 0.98 to 1.0 within a single day. Trained on Monday to Wednesday, it reaches 0.83 on DDoS and 0.98 on PortScan. It still fails on Bot and Infiltration.

## Limits

- Port scans are missed by design. Each probe is a one-packet flow, and flows under 5 packets are not scored. Catching scans needs per-source features, such as distinct ports contacted per second, which this version does not have.
- The numbers above come from CICFlowMeter's flow statistics, not from packets. The packet-level path is `scripts/evaluate_pcap.py`, and these results do not use it.
- One training day, one dataset and one detector.
- The synthetic evaluation is a simulation and stays in the repository only as a pipeline check.
