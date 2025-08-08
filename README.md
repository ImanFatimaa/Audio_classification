# Audio Classification

## Abstract
This project focuses on developing a system capable of differentiating between various audio signals using signal processing and machine learning techniques. The goal is to classify audio signals into three categories: **Speech**, **Music**, and **Noise**. By implementing algorithms for filtering, pitch detection, and audio feature extraction, the project aims to provide a foundational understanding of signal processing and classification tasks.

## Objectives
- **Understand Sound Signals**: Learn about ECG signals and their significance in monitoring heart activity, focusing on identifying R-peaks within the QRS complex.  
- **Signal Pre-processing**: Apply filtering and data augmentation techniques to classify the signal into voice, music, and noise through pitch detection and information.  
- **Pitch Detection**: Implement algorithms to accurately detect and shift pitch.  
- **Audio Classification**: Classify the sounds into three broad categories: Speech, Music, and Noise.  

## Software
- MATLAB R2024a

## Libraries
- Audio Toolbox
- Deep Learning Toolbox
- Signal Processing Toolbox
- Statistics and Machine Learning Toolbox
- Symbolic Math Toolbox

---

## Research and Literature

### Filters
A bandpass filter allows signals within a selected range of frequencies to be heard or decoded, while preventing signals at unwanted frequencies from getting through.  
Signals at frequencies outside the band can saturate or damage the receiver.

**Types:**
- Low-pass filters: allow low frequencies.
- High-pass filters: allow high frequencies.
- Band-pass filters: allow a specific range of frequencies.

**Purpose:** Improve signal clarity by reducing noise and irrelevant components.  
**Implementation:** Applied during data preprocessing to enhance audio quality.

---

### Zero-Crossing Rate (ZCR)
The ZCR of an audio frame is the rate of sign-changes of the signal during the frame.  
**Importance:** Used in speech recognition and music information retrieval, useful in classifying percussive sounds.  
**Formula:** Count the number of zero crossings within a frame.  
**Application:** Differentiate between categories where signal frequency patterns matter, such as Speech and Noise.

---

### RMS Value
Root Mean Square measures the average loudness of an audio signal over time.  
**Significance:** Represents perceived loudness better than peak levels.  
**Application:** Used in neural network classification.

---

### Energy of Signal Tone
Measures total magnitude (loudness) of the signal, often in dB.  
**Usage:** Distinguishes noisy from meaningful sounds.  
**Implementation:** Normalized for fair comparison across audio lengths.

---

### Spectral Centroid
Indicates where the “center of mass” of the spectrum is located.  
**Usage:** Measures musical timbre.  
**Formula:** Weighted mean of frequencies from the Fourier transform.

---

### Spectrogram
A visual representation of signal strength over time across frequencies.  
**Features:** Depends on FFT length, frame size, window type, and sampling frequency.

---

## Pitch Detection Algorithms

### 1. Autocorrelation Method
- Measures similarity of the signal with a delayed version of itself.
- Finds pitch by identifying the lag of the strongest correlation peak.

### 2. Cepstrum Method
- Applies log magnitude of the Fourier transform followed by inverse Fourier transform.
- Highlights periodicities in the signal for pitch estimation.

### 3. AMDF Method
- Computes average magnitude differences between the signal and its shifted versions.
- Finds pitch based on the minimum AMDF value.

---

## Mel-Frequency Component Detection (MFCC)
MFCCs represent timbral characteristics of a signal. Steps:
1. **Hamming Windowing** – reduces spectral leakage.  
2. **Short-Time Fourier Transform (STFT)** – computes frequency content per frame.  
3. **Power Spectrum Calculation** – squares magnitude of STFT.  
4. **Mel Filter Bank Application** – applies perceptually scaled filters.  
5. **Logarithmic Compression** – simulates human loudness perception.  
6. **Discrete Cosine Transform (DCT)** – decorrelates features.  
7. **Feature Selection** – retains first 12–13 coefficients.

---

## Neural Network
Artificial Neural Network (ANN) learns patterns from data for classification.

**Feedforward Neural Network (FNN) Structure:**
- Input Layer – receives features.
- Hidden Layers – learn complex patterns using activation functions (Sigmoid, Tanh, ReLU, Leaky ReLU).
- Output Layer – outputs class probabilities.

---

## Feature Extraction Technique
Features used:
- **Zero Crossing Rate**
- **Energy**
- **Spectral Centroid**
- **RMS Value**

**Classification Rules:**
- **Speech**: Low ZCR, moderate energy, low spectral centroid.
- **Music**: Higher ZCR, higher spectral centroid, variable energy.
- **Noise**: Very high ZCR, high/constant energy, less distinct spectral centroid.

---

## Dataset
**UrbanSound8K** dataset reorganized into folders by label for easier preprocessing and training.

---

## Noise Models
Simulated noise to test model robustness:
- **Rayleigh Noise** – models multipath fading in non-line-of-sight conditions.
- **Nakagami-m Noise** – models different fading severities (m > 1: light fading, m < 1: heavy fading).

**SNR Values:** 10, 20, and 30 dB to represent varying noise levels.
