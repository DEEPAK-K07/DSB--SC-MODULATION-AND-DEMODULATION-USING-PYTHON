# DSB--SC-MODULATION-AND-DEMODULATION-USING-PYTHON

__AIM__:

To generate a Double Sideband Suppressed Carrier (DSB-SC) signal in Python (Google Colab), transmit it (optionally add noise), and recover the message using coherent (synchronous) demodulation with a low-pass filter. Observe time and frequency domain waveforms and measure demodulation performance

__APPARATUS REQUIRED__:

Google Colab (or any Python environment)

Python libraries: numpy, matplotlib, scipy (scipy.signal)

__Theory__:

DSB-SC signal: s(t) = m(t) · cos(2πf_c t)
Coherent demodulation: multiply received s(t) by a synchronized carrier cos(2πf_c t) then low-pass filter (LPF) to remove double-frequency components:

r(t) = s(t)·cos(2πf_c t) = m(t)·cos²(2πf_c t) = 0.5 m(t) + 0.5 m(t)·cos(4πf_c t)
LPF extracts 0.5·m(t) → scale by 2 to recover m(t).

__Procedure__:

1) Import libraries and set parameters
2) Define message and carrier signals
3) Generate DSB-SC signal (modulation)
4) View spectra (FFT) of message and DSB-SC
5) (Optional) Add noise
6) Coherent demodulation (multiply by synchronized carrier)
7) Low-pass filter to recover message

__Program__:
```c
# DSB SC USING PYTHON


import numpy as np
import matplotlib.pyplot as plt

Am = 15.3       # Amplitude of message signal
Ac = 30.6       # Amplitude of carrier signal
fm = 560     # Frequency of message signal
fc = 5600    # Frequency of carrier signal
fs = 90000  # Sampling frequency

t=np.arange(0, 3/fm, 1/fs)

m = Am*np.cos(2*3.14*fm*t)
plt.subplot(3,1,1)
plt.plot(t,m)

c = Ac*np.cos(2*3.14*fc*t)
plt.subplot(3,1,2)
plt.plot(t,c)

s1=(Ac+m)*np.cos(2*3.14*fc*t)
s2=(Ac-m)*np.cos(2*3.14*fc*t)

s=s1-s2
plt.subplot(3,1,3)
plt.plot(t,s)

```

__Tabulation__:

![WhatsApp Image 2025-11-20 at 21 18 40_59523a6e](https://github.com/user-attachments/assets/bd3f9c63-d7b3-4fa5-8c23-85299784becb)


__Output__:

<img width="630" height="469" alt="download (1)" src="https://github.com/user-attachments/assets/887ebb03-aed5-4056-a65f-ba0ed2f9ff39" />


__Result__:

The message signal, carrier signal, and phase/modulated (PM) signal will be display ed in modulated signal variations of the separate plots. The will show phase corresponding to the amplitude message signal.
