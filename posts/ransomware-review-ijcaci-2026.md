# A thematic review of ransomware detection, forensics and recovery

## What the paper is

"Towards Intelligent Ransomware Defence: A Computational-Intelligence-Driven Thematic Review of Detection, Forensics, and Recovery" was accepted at IJCACI 2026 and presented in July 2026. I am first author. I wrote it under the guidance of Prof. Merry KP, the second author. The publishing contract is signed and the paper is not in print yet.

## Method

I started from 87 candidate articles and narrowed them to 14 peer-reviewed studies published between January 2021 and April 2025. I coded each study along seven computational-intelligence themes: threat modelling and game theory, host and network forensics, machine-learning detection surveys, log and timeline analytics, unsupervised latent-space modelling, LLM-assisted incident response, and provenance-based recovery. For each theme I recorded the method, the evaluation metrics, the tools used, the MITRE ATT&CK phases covered and the open gaps.

## What it found

- The highest reported machine-learning detection accuracies come from datasets that predate 2018, cover fewer than ten ransomware families and include no adversarial robustness test.
- Volatility is the most common forensic tool in the corpus, with four studies. Wireshark, Sysmon, Elasticsearch and GPT-4 each appear in three.
- Coverage is thin at the Credential Access and Exfiltration phases of ATT&CK. Enterprise EDR integration and cross-platform forensic validation are also open.

The paper ends with three research directions: a federated benchmark with many ransomware families, multimodal hybrid transformer models, and recovery pipelines guided by provenance graphs.

## Why it matters to my other work

Detection papers rarely say what evidence is left for an investigator. That gap is where RansomGuard starts.
