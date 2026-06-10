# Digital Modulation and BER Performance Analysis over AWGN

**A MATLAB simulation evaluating the Bit Error Rate (BER) performance of various M-ary modulation schemes over an Additive White Gaussian Noise (AWGN) channel.**

## Overview
This project simulates the complete pipeline of a digital communication system—from random bit generation and symbol mapping to noise addition, demapping, and error calculation. It evaluates the performance of **BPSK, QPSK, 8-PSK, and 16-QAM** modulation techniques, comparing empirical simulated results against theoretical mathematical bounds. It also highlights the performance differences between Gray coding and non-Gray coding in QPSK.

## Features
* **Modulation Schemes Implemented:**
  * BPSK (Binary Phase Shift Keying)
  * QPSK (Quadrature Phase Shift Keying) - *Includes Gray vs. Non-Gray coding comparison*
  * 8-PSK (8-Phase Phase Shift Keying) - *Gray-coded*
  * 16-QAM (16-Quadrature Amplitude Modulation) - *Gray-coded*
* **Channel Modeling:** Custom AWGN channel function scaling noise variance dynamically based on the Signal-to-Noise Ratio ($E_b/N_0$) and modulation order.
* **Data Visualization:** Generates ideal constellation diagrams and noisy scatter plots (at $E_b/N_0 = 7$ dB) to visualize signal degradation.
* **Performance Analysis:** Plots simulated BER vs. Theoretical BER across a sweep of $E_b/N_0$ values (-4 dB to 14 dB) using logarithmic scales.

## Project Structure & Core Functions
The simulation is heavily modularized using custom MATLAB functions to mimic real-world DSP pipelines:

* `groupBitsForMapping(data_bits, M)`: Groups serial binary data into symbols based on the modulation order ($M$).
* `AWGN_Channel(tx_signal, EbNo_dB, Eb, M)`: Simulates the physical transmission medium by calculating noise variance and injecting Gaussian noise into the complex symbol stream.
* `BER_Calculation(demapped_bits, original_bits, N)`: Computes the actual Bit Error Rate by comparing the received bit sequence against the transmitted ground truth.

## Results & Visualizations

* **Constellation Diagrams:** The simulation plots the in-phase (I) and quadrature (Q) components of the transmitted symbols after passing through the AWGN channel.
* **BER Performance Curves:** The generated BER curves perfectly demonstrate that higher-order modulation schemes (like 16-QAM) require a higher $E_b/N_0$ to maintain the same error rate as lower-order schemes (like BPSK), illustrating the classic bandwidth-power tradeoff in telecommunications.

## 💻 How to Run
1. Ensure you have **MATLAB** installed.
2. Clone this repository:
   ```bash
   git clone [https://github.com/ManarKml/digital-modulation-ber.git](https://github.com/yourusername/digital-modulation-ber.git)
3. Open the main script in MATLAB.
4. Run the script. The simulation will process $120,000$ bits and automatically output the scatter plots and BER semi-logarithmic graphs for each modulation technique.
