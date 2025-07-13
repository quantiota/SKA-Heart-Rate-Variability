# BITalino Integration for SKA-HRV

This folder contains the code and setup instructions to stream ECG data from a BITalino (r)evolution Board Kit via **USB** and apply real-time **Structured Knowledge Accumulation (SKA)** learning.



## Requirements

* BITalino (r)evolution Board Kit (BLE/BT with USB)
* Python 3.8+
* `pybitalino` library



## Connection

Use USB connection for stable, lossless data:

* Linux: `/dev/ttyUSB0`
* Windows: `COM3` or similar

Avoid BLE due to packet drops in real-time streaming.



## Quick Start

```bash
pip install -r requirements.txt
python ska_stream.py
```



## Output

* Logs ECG signal + entropy
* Sends SKA state to QuestDB
* Grafana dashboard integration



## Technical Specifications

* **Sampling Rate**: 1000 Hz (recommended for HRV)
* **Resolution**: 10-bit ADC
* **Channels**: ECG (A1), optional EDA (A2), EMG (A3)
* **Data Format**: Raw voltage values for SKA processing



## Why BITalino for SKA-HRV?

* **Raw signal access**: Calculate entropy on actual ECG waveform
* **High-frequency sampling**: Capture R-wave timing with millisecond precision
* **No preprocessing**: Apply SKA to unfiltered cardiac data
* **Multi-modal**: Combine ECG + EDA entropy patterns



## Data Flow

```text
BITalino USB → Raw ECG samples → SKA entropy calculation → HRV regime detection → QuestDB logging → Grafana visualization
```





*SKA + BITalino bridges physiological data and information-theoretic learning in real-time.*
