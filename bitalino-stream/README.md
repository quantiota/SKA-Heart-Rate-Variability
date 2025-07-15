# BITalino Integration for SKA-HRV

**Real-Time ECG Entropy Learning with Structured Knowledge Accumulation (SKA)**

This module connects the **BITalino (r)evolution Board Kit** via USB for real-time ECG signal acquisition, directly applying the **SKA entropy learning framework** to uncover hidden physiological regimes in raw heart signals.


## Requirements

- BITalino (r)evolution Board Kit (BLE/BT with USB cable)
- Python ≥ 3.8
- `pybitalino` library (`pip install pybitalino`)
- SKA HRV processing modules (from this repo)
- [Optional] QuestDB + Grafana setup for visualization



## Connection Setup

> For stable real-time processing, **USB** is preferred over BLE (Bluetooth), which may drop packets.

- **Linux**: `/dev/ttyUSB0`
- **Windows**: `COM3` or similar (check Device Manager)

Avoid BLE due to packet drops in real-time streaming.



```bash
git clone https://github.com/quantiota/SKA-Heart-Rate-Variability.git
cd SKA-Heart-Rate-Variability/bitalino
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



## Classical HRV Discards 99% of the ECG Signal

Most HRV research reduces the ECG to just **RR intervals** — losing nearly all waveform complexity:

* Only beat-to-beat intervals are analyzed
* Transient changes and fine-scale dynamics are ignored
* Entropy cannot be measured directly

**SKA is different**:

* Operates on **raw, high-resolution ECG**
* Tracks **information flow and entropy** in real time
* Reveals **hidden physiological transitions** not accessible via classical HRV


## Data Flow


BITalino USB → Raw ECG samples → SKA entropy calculation → HRV regime detection → QuestDB logging → Grafana visualization






