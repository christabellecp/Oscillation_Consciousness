## Exploring Frequency Comparisons Across Cortex & Phase Synchronization Basis for Consciousness

### 1. Introduction

In recent years, there has been an increase in literature devoted to understanding the functional contributions of neural oscillations. It is suspected that synchronous neural oscillations that occur globally rather than locally give rise to conscious awareness (Ward, L.M., 2003). While there are research that explores whether or not the unresponsiveness that arises from anesthesia could be equivalent to unconsciousness, we're working under the assumption that anesthesia induces an unconscious state (Michael T. Alkire, Anthony G. Hudetz, Giulio Tononi, 2008). Anesthesia is "commonly used as a model of slow wave sleep, [...] as ketamine-xylazine anesthesia reproduces the main features of sleep slow oscillation.” Additionally, slow waves are often "associated with diminished consciousness even in the presence of high gamma activity" (Chauvette, S., Crochet, S., et. al., 2011; Murphy, M., Bruno, M. A., et. al., 2011). A survey of sleep research presents many relationships between different cortical areas, frequency bands, and stages of sleep and consciousness. Most notably, the presence of theta oscillations in the cingulate cortex during wakefulness and REM sleep, but not slow-wave sleep (Nishida et al. 2004); wakefulness and  N2 and N3 stages of slow-wave sleep are characterized by slow delta oscillations. Finally, there is high speculation as to whether conscious experience and a sense of agency arises from a gamma-synchronized dendritic web, also known as the "conscious pilot" (Stuart Hameroff, 2009). So we ask: how do oscillations compare during sleep and wakefulness across brain regions; are there neural correlates of consciousness, and if so, how do they manifest as neural oscillations?

### 2. Research Question & Hypothesis

**Research Question:** How do oscillation frequencies compare during an anesthetized state and a wakeful state across the brain regions? Is gamma phase synchronization an oscillatory basis for consciousness? 

**Hypothesis:** Based on prior literature, we hypothesize that lower frequencies will contribute to the anesthetized state more than the awake state. Additionally, we are anticipating that the cingulate region will show “regular and continuous theta oscillation” during the awake state but not during the anesthetized state. Lastly, we expect gamma phase synchronization to be a basis for consciousness, and therefore, have high synchronization across the various regions of the brain during the awake state. Conversely, we do not expect to find this same result in the anesthetized state.

### 3. Methodology
#### 3.1 Dataset Description
The dataset we analyzed is from NeuroTycho titled “Anesthesia and Sleep Task”, an experiment carried out by Yanagawa, T., Chao, Z. C., Hasegawa, N., & Fujii. ECoG data was extracted from monkey cortices, sampled at 1000Hz from 3 different channels (cingulate, temporal cortex and occipital cortex) from electrode numbers 52, 91, 70, respectively. For 5 minutes, the monkey is awake with their eyes open and another 5 minutes the monkey is anesthetized.

<a id='methods'></a>

#### 3.2 Methods & Parameter Decisions
This section displays the algorithms we implemented and the parameters that were selected for each algorithm. 



**Fourier Transform and Power Spectral Density:** The Fourier Transform converts the signal from time domain to frequency domain. We utilized this to find which frequencies contribute most during the awake state and compare that to the sleep state by plotting the power spectral density. The PSD displays the normalized power of each frequency.


**Short Time Fourier Transform:** STFT takes the fourier transform at various windows across time, allowing us to plot the power of each frequency across time using a spectrogram. A known tradeoff between longer and shorter windows is temporal and frequency resolution. We initially decided on a window size of 1 seconds and an overlap of 0.5 seconds as a standard measure. However, upon noticing frequency band spikes at every 50 seconds, we also computed the spectrogram utilizing a window length of 5.0 seconds and overlap of 4.0 seconds. We decided on these parameters because we wanted better frequency resolution to see these frequency band spikes more clearly.


**Filtering and Convolution:** We applied a bandpass filter for each of the brainwaves, decomposing the signal into all of the brainwave components (delta, beta, alpha, etc.) and compared the awake state and sleep state side by side. We wanted to have a visual overview exploring how the various frequency band signals differ from an awake state and anesthetized state.


**Hilbert Transform & Instantaneous Power Signal:** The Hilbert Transform provides the analytic signal by utilizing the Fourier Transform and omitting the negative frequencies in the original data. 


**Instantaneous Power Signal:** The Hilbert Transform allows us to compute the instantaneous power signal of the theta frequency through time in order to gauge whether or not theta oscillations are regular and continuous for all states.  


**Gamma Phase Synchronization:** We extracted the gamma component of each region for the awake state and plotted their instantaneous phases on the same graph to visualize whether or not they overlap. Afterwards, we plotted the synchrony between every two regions, as well as the average synchrony across all brain regions. We repeated this process on the anesthetized data. Finally, we calculated the average of the synchronization, for both states to see whether or not the awake signal has a higher rate of synchronization. This provided insight as to whether or not synchrony in gamma oscillation is, indeed, a basis for consciousness.


### Conclusion & Discussions

Our overall findings initially confirmed our belief that awake states produces higher overall frequencies as compared to anesthetized states. Once we figured out which frequencies specifically contribute to both signals, we found that awake signals contain more powerful frequencies on the range of about 4Hz and above (theta waves and above). This confirms our hypothesis of awake states maintaining a primarily higher range of frequencies, with anesthetized states mainly containing lower-range frequencies (delta waves). A spectrogram revealed that this pattern was consistent across time. However, we noticed that the cingulate region contained spikes at about every 50 seconds where all ranges of frequencies contributed more evenly to the signal. In the temporal and occipital lobe, we found that the delta component in the awake state maintains a higher amplitude than in the anesthetized state. However, the cingulate region differs in that each component seems to contribute equally across both the awake and anesthetized states. Our initial hypothesis proposed that the theta component in the awake state would have a higher-power contribution than in anesthesia, but the data refutes it.

### Limitations
In terms of a basis for consciousness, we were only able to look at three brain regions and therefore, cannot account for additional regions that may contribute to the synchronization rates. Additionally, we were working under the assumption that the Medetomidine-Ketamine anesthesia induces a state of slow wave sleep, however, the research we found was only about XylazineKetamine. These anesthesia methods may work differently. We are also assuming this state reflects a lack of consciousness and this is currently still under investigation. Lastly, our lack of deep domain knowledge of neuroscience may contribute to certain discrepancies in the data. 

### References
1. Alkire, M. T., Hudetz, A. G., & Tononi, G. (2008). Consciousness and anesthesia. Science, 322(5903), 876-880.
2. Chauvette, S., Crochet, S., Volgushev, M., & Timofeev, I. (2011). Properties of slow oscillation during slow-wave sleep and anesthesia in cats. Journal of Neuroscience, 31(42), 14998-15008.
3. Groppe, D. M., Bickel, S., Keller, C. J., Jain, S. K., Hwang, S. T., Harden, C., & Mehta, A. D. (2013). Dominant frequencies of resting human brain activity as measured by the electrocorticogram. Neuroimage, 79, 223-233.
4. Hameroff, S. (2010). The “conscious pilot”—dendritic synchrony moves through the brain to mediate consciousness. Journal of biological physics, 36(1), 71-93.
5. Igawa, M., Atsumi, Y., Takahashi, K., Shiotsuka, S., Hirasawa, H., Yamamoto, R., ... & Koizumi, H.  (2001). Activation of visual cortex in REM sleep measured by 24‐channel NIRS imaging. Psychiatry and clinical neurosciences, 55(3), 187-188.
6. MacKay, W. A. (1997). Synchronized neuronal oscillations and their role in motor processes. Trends in  cognitive sciences, 1(5), 176-183.
7. Nishida, M., Hirai, N., Miwakeichi, F., Maehara, T., Kawai, K., Shimizu, H., & Uchida, S. (2004). Theta oscillation in the human anterior cingulate cortex during all-night sleep: an electrocorticographic study. Neuroscience research, 50(3), 331-341.
