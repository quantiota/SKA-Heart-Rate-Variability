
# BITalino Integration for SKA-HRV

**Real-Time ECG Entropy Learning with Structured Knowledge Accumulation (SKA)**

This module connects the **BITalino (r)evolution Board Kit** via USB for real-time ECG signal acquisition, directly applying the **SKA entropy learning framework** to uncover hidden physiological regimes in raw heart signals.



##  Requirements

- BITalino (r)evolution Board Kit (BLE/BT with USB cable)
- Python ≥ 3.8
- `pybitalino` library (`pip install pybitalino`)
- SKA HRV processing modules (from this repo)
- [Optional] QuestDB + Grafana setup for visualization



##  Connection Setup

> For stable real-time processing, **USB** is preferred over BLE (Bluetooth), which may drop packets.

- **Linux**: `/dev/ttyUSB0`
- **Windows**: `COM3` or similar (check Device Manager)



##  Quick Start

```bash
git clone https://github.com/quantiota/SKA-Heart-Rate-Variability.git
cd SKA-Heart-Rate-Variability/bitalino
pip install -r requirements.txt
python ska_stream.py
````

This script will:

* Stream ECG in real-time from BITalino
* Compute entropy via the SKA learning engine
* Log entropy transitions to QuestDB
* \[Optional] Update Grafana dashboard



##  Output

* Raw ECG signal logs (CSV or QuestDB stream)
* Real-time SKA entropy scores
* Regime labels (neutral, stress, recovery, etc.)
* Timestamped event logs for visualization and analysis

---

##  Technical Specifications

| Feature           | Value                                 |
| ----------------- | ------------------------------------- |
| Sampling Rate     | 1000 Hz (recommended for HRV)         |
| ADC Resolution    | 10-bit                                |
| Channels Used     | A1 (ECG), optional A2 (EDA), A3 (EMG) |
| Data Format       | Raw voltage per timestamp             |
| Signal Processing | None (SKA learns from raw waveform)   |



##  Why BITalino for SKA-HRV?

> Traditional HRV methods simplify ECG into RR intervals, discarding most of the physiological signal. SKA takes a radically different approach:

### Classical HRV:

* Reduces signal to beat-to-beat intervals
* Ignores waveform shape and transient dynamics
* Uses fixed-window statistical summaries

### SKA Entropy Learning:

* Learns from **raw, full-resolution ECG**
* Captures **nonlinear information flow**
* Detects **entropy transitions** in real-time
* Supports **multi-modal learning** (ECG + EDA)



##  Data Flow Diagram

```text
BITalino USB
     ↓
Raw ECG Signal
     ↓
SKA Entropy Processor (Python)
     ↓
Entropy Score + Regime State
     ↓
QuestDB (Time Series Storage)
     ↓
Grafana (Live Visualization)
```



##  Integration Goals

This module is part of the larger **SKA-HRV** initiative to redefine how physiological data is analyzed, monitored, and understood using entropy-first learning frameworks.












