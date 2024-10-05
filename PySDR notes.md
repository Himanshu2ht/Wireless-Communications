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
<img src="https://pysdr.org/_images/fft-python5.png" widht="500" height="500"/>
<br>

# IQ Sampling
IQ sampling is the form of sampling that an SDR performs.

We record the value of s(t) at regular intervals of T seconds, known as the `sample period`.

The frequency at which we sample, i.e., the number of samples taken per second, is simply 1/T. We call this the `sample rate`, F(s), and its the inverse of the sample period.

## Nyquist Sampling
For a given signal, the big question often is how fast must we sample?

The `Nyquist Rate` is the minimum rate at which a (finite bandwidth) signal needs to be sampled to retain all of its information.

If we don’t sample fast enough we get something called `aliasing`.

So we have to sample at more then twice the maximum frequency of the signal:  
<br>
<img src="https://pysdr.org/_images/nyquist_rate.png" widht="300" height="300"/>
<br>
What our SDRs do (and most receivers in general) is filter out everything above Fs/2 right before the sampling is performed. If we attempt to receive a signal with too low a sample rate, that filter will chop off part of the signal.

## Quadrature Sampling
`Quadrature` - It refers to two waves that are 90 degrees out of phase.  
<br>
<img src="https://pysdr.org/_images/IQ_wave.png" widht="300" height="300"/>
<br>  
We will use I for the cos() and Q for the sin():

I cos(2πft)

Q sin(2πft)

We call the cos() the “in phase” component, hence the name I, and the sin() is the 90 degrees out of phase or “quadrature” component, hence Q.

The important takeaways are that when we add the cos() and sin(), we get another pure sine wave with a different phase and amplitude.

This is all a result of the trigonometric identity: acos(x) + bsin(x) = Acos(x- Ω).

The “utility” of this behavior is that we can control the phase and amplitude of a resulting sine wave by adjusting the amplitudes I and Q (we don’t have to adjust the phase of the cosine or sine).
For example, we could adjust I and Q in a way that keeps the amplitude constant and makes the phase whatever we want.

As a transmitter this ability is extremely useful because we know that we need to transmit a sinusoidal signal in order for it to fly through the air as an electromagnetic wave.

It will look something like this:  
<br>
<img src="https://pysdr.org/_images/IQ_diagram.png" widht="300" height="300"/>

We only need to generate one sine wave and shift it by 90 degrees to get the Q portion.

## Complex Numbers in FFTs
The FFT figures out which frequencies exist in that set of samples (the magnitude of the FFT indicates the strength of each frequency).  

But what the FFT also does is figure out the delay (time shift) needed to apply to each of those frequencies, so that the set of sinusoids can be added up to reconstruct the time-domain signal.  

That delay is simply the phase of the FFT. The output of an FFT is an array of complex numbers, and each complex number gives you the magnitude and phase, and the index of that number gives you the frequency.  

If you generate sinusoids at those frequencies/magnitudes/phases and sum them together, you’ll get your original time domain signal

## Receiver Side
Using IQ sampling, the diagram looks like this on Receiver side:  
<br>
<img src="https://pysdr.org/_images/IQ_diagram_rx.png" widht="300" height="300"/>

What we do is sample the I and Q branches individually, using two ADCs, and then we combine the pairs and store them as complex numbers.  
In other words, at each time step, you will sample one I value and one Q value and combine them in the form I + jQ (i.e., one complex number per IQ sample).

### Receiver Architectures
<img src="https://pysdr.org/_images/receiver_arch_diagram.svg" widht="800" height="800"/>
<br>
<b>LNA - Low-noise amplifier</b>
<br>
<b>IF - Intermediate frequency</b>
<br>

### Baseband and Bandpass Signals
We refer to a signal centered around 0 Hz as being at `baseband`.  
Conversely, `bandpass` refers to when a signal exists at some RF frequency nowhere near 0 Hz, that has been shifted up for the purpose of wireless transmission.  
  
There is no notion of a “baseband transmission”, because you can’t transmit something imaginary.

## Generating a signal and noise in Python

Here is a full code example that includes generating a signal (complex exponential at 50 Hz) and noise.

```bash
import numpy as np
import matplotlib.pyplot as plt

Fs = 300 # sample rate
Ts = 1/Fs # sample period
N = 2048 # number of samples to simulate

t = Ts*np.arange(N)
x = np.exp(1j*2*np.pi*50*t) # simulates sinusoid at 50 Hz

n = (np.random.randn(N) + 1j*np.random.randn(N))/np.sqrt(2) # complex noise with unity power
noise_power = 2
r = x + n * np.sqrt(noise_power)

PSD = np.abs(np.fft.fft(r))**2 / (N*Fs)
PSD_log = 10.0*np.log10(PSD)
PSD_shifted = np.fft.fftshift(PSD_log)

f = np.arange(Fs/-2.0, Fs/2.0, Fs/N) # start, stop, step

plt.plot(f, PSD_shifted)
plt.xlabel("Frequency [Hz]")
plt.ylabel("Magnitude [dB]")
plt.grid(True)
plt.show()
```
#### Output:
<img src="https://pysdr.org/_images/fft_example1.svg" widht="500" height="500"/>
