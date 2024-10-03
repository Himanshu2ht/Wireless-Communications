## SDR- Software-Defined Radio:
It refers to using software to perform signal processing tasks that were traditionally performed by hardware, specific to radio/RF applications.  
<br>

**DSP- Digital Siginal Processing**  
<br>

## Fourier Series:
When we break a signal down into its composite sine waves, we call it a Fourier series.  
<br>
<img src="https://pysdr.org/_images/summing_sinusoids.svg" widht="300" height="300"/>

## Fourier Transform:
When we go from the time domain to the frequency domain and back is called the Fourier Transform.  
It is defined as follows:  
<br>
<img src="https://github.com/Himanshu2ht/Anonymous/blob/main/Screenshot%20(12).png" widht="300" height="300"/>
<br>

## Fast Fourier Transform:
The Fast Fourier Transform (FFT) is simply an algorithm to compute the discrete Fourier Transform.
<br>

### FFT in Python:
```bash
import numpy as np
import matplotlib.pyplot as plt

Fs = 1 # Hz
N = 100 # number of points to simulate, and our FFT size

t = np.arange(N) # because our sample rate is 1 Hz
s = np.sin(0.15*2*np.pi*t)
S = np.fft.fftshift(np.fft.fft(s))
S_mag = np.abs(S)
S_phase = np.angle(S)
f = np.arange(Fs/-2, Fs/2, Fs/N)
plt.figure(0)
plt.plot(f, S_mag,'.-')
plt.figure(1)
plt.plot(f, S_phase,'.-')
plt.show()
```
<br>
<img src="https://pysdr.org/_images/fft-python5.png" widht="300" height="300"/>
<br>

