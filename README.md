Audio Classification Abstract: This project focuses on developing a
system capable of differentiating between various audio signals using
signal processing and machine learning techniques. The goal is to
classify audio signals into three categories: Speech, Music, and Noise.
By implementing algorithms for filtering, pitch detection, and audio
feature extraction, the project aims to provide a foundational
understanding of signal processing and classification tasks.\
Objective: • Understand Sound Signals: Learn about ECG signals and their
significance in monitoring heart activity, focusing on identifying
R-peaks within the QRS complex.\
• Signal Pre-processing: Apply filtering and data augmentation
techniques to classify the signal into voice, music and noise through
pitch detection and information. • Pitch Detection: Implement algorithms
to accurately detect and shift pitch.\
• Audio Classification: Classify the sounds into three broad categories
as 1. Speech, 2. Music and 3. Noise.\
Software: • MATLAB R2024a Libraries: • Audio Toolbox • Deep Learning
Toolbox • Siignal Processing Toolbox • Statistics and Machine Learning
Toolbox • Symbolic Math Toolbox

Research and Literature • Filters: A bandpass filter allows signals
within a selected range of frequencies to be heard or decoded, while
preventing signals at unwanted frequencies from getting through. Signals
at frequencies outside the band which the receiver is tuned at can
either saturate or damage the receiver. • Types: o Low-pass filters to
allow low frequencies. o High-pass filters to allow high frequencies. o
Band-pass filters to allow a specific range of frequencies.

• Purpose: Improve signal clarity by reducing noise and irrelevant
components. • Implementation: Applied during data preprocessing to
enhance audio quality.

• Zero-Crossing Rate: The Zero-Crossing Rate (ZCR) of an audio frame is
the rate of sign-changes of the signal during the frame. In other words,
it is the number of times the signal changes value, from positive to
negative and vice versa, divided by the length of the frame. Importance:
Its value has been widely used in both speech recognition and music
information retrieval, being a key feature to classify percussive
sounds. • Formula: Count the number of zero crossings within a frame. •
Application in the Project: Used to differentiate between categories
where signal frequency patterns play a significant role, such as Speech
and Noise.

• RMS Value: RMS, or Root Mean Square, is a mathematical term that
measures the average loudness of an audio signal over time. It's
considered a more accurate representation of how loud a sound is
perceived than peak levels. • Significance: Indicates the loudness or
energy content of a signal. • Application: RMS value was calculated for
all signal frames classifying audio with neural networks.

• Energy of Signal Tone: The energy of a signal tone is the total
magnitude of the signal, which is roughly equivalent to how loud the
signal is. The energy of a signal is often measured in decibels (dB),
which is a logarithmic measure of energy. • Usage: Essential for
distinguishing between noisy and meaningful sounds. • Implementation:
The energy metric was normalized to ensure fair comparison across
varying audio lengths.

• Spectral Centroid: The spectral centroid is a measure used in digital
signal processing to characterize a spectrum. It indicates where the
center of mass of the spectrum is located.\
• Usage: it is widely used in digital audio and music processing as an
automatic measure of musical timbre.\
• Formula: It is calculated as the weighted mean of the frequencies
present in the signal,\
determined using a Fourier transform, with their magnitudes as the
weights.

• Spectrogram: In signal processing, a spectrogram is a visual
representation of how the strength of a signal varies over time and
across frequencies. • Application: A spectrogram is a visual way of
representing the signal strength, or "loudness", of a signal over time
at various frequencies present in a particular waveform. • Features: it
depends on all three parameters (FFT length, Frame size, Window) and the
sampling frequency of the sound file.

• Pitch Detection Algorithm: Pitch is an auditory sensation in which a
listener assigns musical tones to relative positions on a musical scale
based primarily on their perception of the frequency of vibration (audio
frequency). We primarily used three methods for Pitch Detection later
compared them to find the best one.

• Autocorrelation Method:\
This technique calculates the autocorrelation of the audio signal, which
measures the similarity of the signal with a delayed version of itself.
It identifies the pitch by finding the peak in the autocorrelation
function within a specified range of lags corresponding to possible
pitch frequencies. The method assumes that a periodic signal, like a
musical tone or speech, will have a strong correlation with itself at
regular intervals. After computing the autocorrelation, the pitch
frequency is calculated as the inverse of the pitch period (the time
between peaks). A plot of the autocorrelation function is generated to
visualize the correlation across different time delays.

• Cepstrum Method:\
The cepstrum method transforms the audio signal into the cepstral domain
by first taking the logarithm of the magnitude of the Fourier transform
of the signal, followed by an inverse Fourier Transform. The resulting
cepstrum highlights periodicities in the signal, which correspond to
pitch. The peak in the cepstrum represents the pitch period, and the
pitch frequency is calculated by taking the inverse of the corresponding
quefrency. A plot of the cepstrum is generated to show the amplitude
across different quefrency values. This method is particularly useful
for signals with periodic components.

• AMDF Method:\
The Average Magnitude Difference Function (AMDF) method measures the
similarity between the signal and its shifted versions. It works by
computing the sum of absolute differences between the original signal
and the shifted signal for each possible lag (time shift). The pitch is
determined by identifying the lag with the minimum AMDF value,
corresponding to the pitch period. The pitch frequency is then
calculated as the inverse of this period. A plot of the AMDF values is
displayed to illustrate how the difference function behaves across
different lags.

• Mel-Frequency Component Detection Algorithm: Mel-frequency cepstral
coefficients (MFCCs) represent timbral information of a signal and are
computed by converting Fourier coefficients to Mel-scale, logarithmizing
the obtained vectors, and decorrelating them by DCT to remove redundant
information. • Features: MFCC are popular features extracted from speech
signals for use in recognition tasks. In the source-filter model of
speech, MFCC are understood to represent the filter (vocal tract).\
• Technique Used:\
• Hamming Windowing Hamming windowing is a smoothing technique applied
to each frame of the audio signal before performing a Fourier Transform.
It tapers the edges of the frame to reduce discontinuities at the
boundaries. It Prevents spectral leakage, which can occur when abrupt
transitions at the frame edges introduce artificial frequency components
in the Fourier analysis.

• Short-Time Fourier Transform (STFT) The audio signal is divided into
overlapping frames, and for each frame, a Short Time Fourier Transform
(STFT) is performed after applying a Hamming window to reduce edge
effects. The STFT represents the frequency content of the signal at
different time points.

• Power Spectrum Calculation The power spectrum is calculated by
squaring the magnitude of the STFT, keeping only the positive
frequencies. This represents how much energy is present at each
frequency.

• Mel Filter Bank Application A Mel filter bank is created, which is a
set of triangular filters spaced according to the Mel scale. The Mel
scale is a perceptual scale of pitches, which is more aligned with human
auditory perception than the linear frequency scale. The function
melFilterBankGenerator generates these filters based on the sample rate
and FFT size.

• Logarithmic Compression A logarithmic transformation is applied to the
Mel spectrum to simulate human auditory perception, where the perception
of loudness is logarithmic. This step compresses the range of values and
helps in better feature representation.

• Discrete Cosine Transform (DCT) The Discrete Cosine Transform (DCT) is
applied to the logarithmic Mel spectrum to decorrelate the features. DCT
compresses the information into a smaller number of uncorrelated
coefficients. The first few coefficients (typically 12 or 13) capture
the most significant features of the audio signal.

• Feature Selection Feature selection is the process of choosing a
subset of the most relevant features (or coefficients) from the entire
set of extracted features. After applying the DCT, only the first 12 or
13 coefficients (representing the most significant spectral features)
are retained. These lower-order coefficients capture the broad spectral
shape, while higher-order coefficients often represent fine details that
are less useful for tasks like speech recognition or audio
classification. • Neural Network: A neural network (also called an
artificial neural network or ANN) is an adaptive system that learns by
using interconnected nodes or neurons in a layered structure that
resembles a human brain. A neural network can learn from data, so it can
be trained to recognize patterns, classify data, and forecast future
events. • Working: A neural network breaks down the input into layers of
abstraction. It can be trained using many examples to recognize patterns
in speech or images just as the human brain does. The neural network
behavior is defined by the way its individual elements are connected and
by the strength or weights, of those connections.

• Audio Classification: For audio classifications, we applied two
techniques. One is by extracting features from audio signal and other is
using Neural Networks. • Feedforward Neural Network:\
FNN is a type of artificial neural network where connections between the
nodes do not form cycles. The network consists of an input layer, one or
more hidden layers, and an output layer. Information flows in one
direction---from input to output---hence the name "feedforward." •
Structure: o Input Layer: The input layer consists of neurons that
receive the input data. Each neuron in the input layer represents a
feature of the input data. o Hidden Layers: One or more hidden layers
are placed between the input and output layers. These layers are
responsible for learning the complex patterns in the data. Each neuron
in a hidden layer applies a weighted sum of inputs followed by a
non-linear activation function. o Output Layer: The output layer
provides the final output of the network. The number of neurons in this
layer corresponds to the number of classes in a classification problem
or the number of outputs in a regression problem.

• Activation Functions Activation functions introduce non-linearity into
the network, enabling it to learn and model complex data patterns.
Common activation functions include: o Sigmoid:
σ(x)=σ(x)=11+e−xσ(x)=1+e−x1 o Tanh:
tanh(x)=ex−e−xex+e−xtanh(x)=ex+e−xex−e−x o ReLU (Rectified Linear Unit):
ReLU(x)=max⁡(0,x)ReLU(x)=max(0,x) o Leaky ReLU: Leaky
ReLU(x)=max⁡(0.01x,x)Leaky ReLU(x)=max(0.01x,x)

• Feature Extraction Technique:\
In this technique, we calculated the Zero Crossing Rate, Energy,
Spectral Centroid and\
rmsValue and then compared them with threshold value for Speech, Noise
and Music and classified the audio signal on the basis of it. • Speech:
It has typically low ZCR, as human tends to have smoother conversation,
has moderate Energy and a lower Spectral Centroid. • Music: It has
higher ZCR due to the presence of sharp, percussive sounds and higher
Spectral Centroid with varying Energy. • Noise: It has a very higher
ZCR, constant or high Energy and a less distinct Spectral Centroid as
its energy is spread more uniformly across frequencies.

• Data Set: The Kaggle UrbanSound8K dataset was reorganized into a new
folder structure, grouping audio files based on their corresponding
labels. This rearrangement streamlines data preprocessing for training
and evaluation, making it easier to feed labeled data directly into a
machine learning or neural network model. • Importance: The restructured
dataset simplifies the training process by clearly mapping audio files
to labels, enabling efficient data handling. It ensures compatibility
with supervised learning frameworks and improves focus on detecting
relevant categories. • Noise Model Noise refers to unwanted
modifications introduced to a source signal during the capture, storage,
transmission, or processing of its information. Here we employed two
commonly used noise models---Rayleigh and Nakagami-m---to simulate
different types of noise and assess the robustness of our model under
various noisy conditions. • Rayleigh Noise Model: The Rayleigh noise
model is often used to describe fading channels where the signal
undergoes multipath propagation. It assumes that the amplitude of the
received signal follows a Rayleigh distribution, which is typically
applicable for environments with scattered, non-line-of-sight signals. •
Nakagami-m Noise Model: The Nakagami-m distribution is more general than
Rayleigh and can model different types of fading, including both light
and heavy fading conditions. It is defined by a parameter "m" that
controls the severity of fading: o When m=1m = 1m=1, the Nakagami-m
model becomes equivalent to the Rayleigh distribution. o Values of m\>1m
\> 1m\>1 indicate less severe fading, while values of m\<1m \< 1m\<1
model more severe fading (in environments with heavy multipath).

• Sound Models: SNR values (10, 20, and 30 dB) are used to simulate
varying noise levels, where a higher SNR indicates a cleaner signal
(less noise), and a lower SNR represents a noisier signal.

