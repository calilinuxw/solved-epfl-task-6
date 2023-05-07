Download Link: https://assignmentchef.com/product/solved-epfl-task-6
<br>
In the previous Section 5 we have seen that the signal undergoes a random phase-rotation in the channel. In practical radio communication systems there is an additional effect a communication systems engineer has to take into account. The magnitude of the signal varies randomly over time. This effect is called fading. The reason for fading can be divided in two groups:

<ul>

 <li>Large-scale fading, slow varying attenuation of the signal due to the distance to the transmitter (path loss) or large obstacles (mountains etc.).</li>

 <li>Small-scale fading, fast changing signal strength due to constructive and destructive interference.</li>

</ul>

Large-scale fading is already addressed in our model by means of the SNR value. Throughout this exercise we are only interested in dealing with the small-scale fading case. You have probably already observed small-scale fading as large variation of the signal strength of your radio or cell phone.

The presence of small-scale fading changes the input-output relation from the pure additive white Gaussian-noise (AWGN) case

y[k] = x[k] + n[k]                                                            (6.1)

to

y[i] = h[k]x[k] + n[k]                                                         (6.2)

where h is a (complex) random variable with certain statistical properties. You will notice that in small-scale fading environment the BER decays much slower with increasing SNR compared to the AWGN case. (Note: Despite the misleading naming there is also an additive white Gaussian noise component in the fading case). The AWGN channel can also be modeled as a fading channel with a deterministic h = 1.

37

<h2>Coherence</h2>

The propagation conditions do not change instantaneously; hence, channel coefficients are usually correlated in time and frequency. This means that if the channel is in a bad condition, then neighboring (in time or frequency) channel coefficients are also very likely in a bad condition.

This correlation of the channel coefficients is usually described by two parameters: The coherence time and the coherence bandwidth. These parameters describe the distance in time/frequency over which the channel changes significantly. While these measures look very intuitive there is no strict definition of how large or likely the change of the channel has to be. There are multiple different definitions of the term. So consider these numbers not as precise values, but as orders of magnitude.

From the viewpoint of the receiver fading can be divided in two scenarios:

<ul>

 <li>Slow fading, the change of the channel condition within your time-span of interest (e.g. one frame) is negligible, but nevertheless has to be taken into account between successive transmission or different channels.</li>

 <li>Fast fading, the change of the channel within your time-span has significant influence on the performance of your system and has to be compensated in your receiver.</li>

</ul>

<h2>Diversity</h2>

In the lecture we saw that the probability of an error becomes significant if the channel coefficient h is below a certain threshold. We sometimes refer to such an event as outage. The probability for an outage event is p<sub>out</sub>. Hence the probability of successful transmission is:

psuccess ≈ 1 − pout

If the same data is sent over L independent channel realizations, then all coefficients have to be in outage for none of the copies to be received with proper signal strength. The probability 38          Chapter6:FadingChannels of successful transmission is therefor much higher and becomes

psuccess ≈ 1 − pout)L

The independence of the realizations is the crucial condition to exploit the full gain of diversity.

<h2>Receive Diversity</h2>

It is possible to obtain diversity on the receiving side without any modifications of the transmitter. One can employ multiple antennas in order to receive the same signal multiple times under different fading conditions. The antennas have to be sufficiently spaced apart so that their distance exceeds the coherence distance. Therefor this is also called space diversity. There are two common schemes to make use of space diversity.

<h3>Antenna Selection Diversity</h3>

Antenna selection diversity is a cheap way to implement receive diversity. It is achieved by attaching two or more sufficiently spaced antennas with a switch to the same receiver. The receiver periodically compares the signal strength at the antennas and selects the strongest signal for reception.

hequivalent = maxh1h2..)                                                        (6.3)

This approach offers the advantage that it is very cheap in terms of hardware costs as only one RX chain is required. On the downside this scheme can not exploit the full possible diversity gain.

<h3>Maximum Ratio Combining</h3>

In the lecture you have also seen a more elaborate way of exploiting receive diversity. A maximum ratio combiner takes advantage of the signal from all receive paths to further increase the diversity gain. We consider the following input-output relation. The scalar equation has now transformed to a vector problem.

<table width="527">

 <tbody>

  <tr>

   <td width="427">y = hx + nA matched filter of the form</td>

   <td width="99">(6.4)</td>

  </tr>

  <tr>

   <td width="427">h∗h<sub>mf </sub>=||h||leads to an equivalent channel of:</td>

   <td width="99">(6.5)</td>

  </tr>

  <tr>

   <td width="427">                                                                    h∗h           h∗h<sub>mf </sub>∗ y =             x +          n = ||h||x + n˜||h||      ||h||</td>

   <td width="99">(6.6)</td>

  </tr>

  <tr>

   <td width="427">h<sub>equivalent </sub>= ||h||</td>

   <td width="99">(6.7)</td>

  </tr>

 </tbody>

</table>

39

<h2>Rayleigh Fading</h2>

A channel model which is often used to describe the effect of fading on the channel is the Rayleigh fading. The channel coefficient is modeled as a complex circular-symmetric Gaussian random variable. h ∼ N 01)              (6.8)

<h3>Your Tasks</h3>

For the next exercise we assume a slow fading channel with Rayleigh Fading with three receive antennas. We assume the exaggerated case where the channel coefficient is constant in magnitude and phase during a frame, but completely independent from the coefficient of any other frame or antenna. To keep the slow fading assumption valid we can only transmit shorter frames.

<ol>

 <li>On the moodle we provide you the symbols task61.mat of an image which has been split in 12 frames. Complete the provided receiver diversityreceiver.m which uses only one antenna. Explain why some parts of the picture appear to be of better quality compared to a non-fading case with the same SNR?</li>

 <li>Extend the frame synchronization code to also provide an estimate of the magnitude of the channel. (Note: Don’t forget that there is already some kind of normalization.)</li>

 <li>Implement an antenna-selection-based diversity receiver which picks always the best antenna. The framework provides the different antenna realizations as rows of the noiseFrame variable.</li>

 <li>Use the QPSK sequence pnsequencefading.mat provided on the moodle to adapt the given framework to perform BER simulations.</li>

 <li>Implement an MRC diversity receiver and compare its BER performance to the antennaselection design you created before.</li>

 <li>Prove that the MRC diversity receiver will always outperform its antenna-selection counterpart in an ideal Rayleigh fading scenario.</li>

</ol>