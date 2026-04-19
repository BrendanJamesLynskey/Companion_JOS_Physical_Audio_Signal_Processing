# Companion to *Physical Audio Signal Processing* by Julius O. Smith III

An interactive, animated companion to Julius O. Smith III's online book
[*Physical Audio Signal Processing*](https://ccrma.stanford.edu/~jos/pasp/).
The wave equation, digital waveguides, Karplus&ndash;Strong, reed and bow
nonlinearities, finite-difference time-domain (FDTD), modal synthesis,
commuted-piano synthesis, and feedback-delay-network reverb &mdash; with every
idea rebuilt as a hand-written JavaScript canvas and Web Audio demo.

**[&rarr; View the Live Guide](https://brendanjameslynskey.github.io/Companion_JOS_Physical_Audio_Signal_Processing/)**

---

## What's Inside

Thirteen chapters walk through the history, mathematics, and synthesis
practice of physical audio modelling, with real-time interactive
visualisations and audio playback throughout.

### 1 &middot; Prologue &mdash; Physics meets DSP
Why physical modelling matters: realism under continuous control, gestural
economy, computational efficiency. Orientation and cross-links to the rest
of the companion-book corpus.

### 2 &middot; A History of the Synthetic Instrument
Illustrated timeline: Helmholtz (1862), Raman (1918), Hiller &amp; Ruiz
(1971), McIntyre &amp; Woodhouse (1979), Karplus &amp; Strong plus Jaffe &amp;
Smith (1983), Cordis-Anima (ACROE), Smith's digital waveguide (1986&ndash;92),
IRCAM Modalys (1989), Yamaha VL1 (1994), commuted piano (Smith &amp; Van
Duyne 1995), Pianoteq (2006), DDSP and neural physical models (2020&ndash;).

### 3 &middot; The 1-D Wave Equation
Full derivation from tension and mass; D'Alembert's travelling-wave
decomposition $y(x,t) = y^{+}(x-ct) + y^{-}(x+ct)$; fixed vs free boundary
conditions. Interactive: release a Gaussian lump in a finite string, toggle
fixed/free at the right end, tune damping, listen to the result.

### 4 &middot; Digital Waveguides
From D'Alembert to two delay lines with $f_s = c/\Delta x$. Boundary
lowpass models frequency-dependent loss. Interactive bowed/plucked
waveguide with pitch, decay, brightness, pick-position controls, and
Web-Audio listen.

### 5 &middot; Karplus&ndash;Strong
The simplest waveguide in the world. Derivation, the 1983 Karplus&ndash;Strong
CMJ paper, and the companion Jaffe&ndash;Smith extensions. Live demo with
noise-burst or impulse excitation, damping and pick-position controls.

### 6 &middot; Reflections and Junctions
Wave impedance, the Fresnel-style scattering at a junction of two
impedances, Kelly&ndash;Lochbaum's three-port scattering matrix. Interactive
impedance-mismatch demo prints live reflection and transmission
coefficients.

### 7 &middot; Bowed Strings
Helmholtz motion, stick-slip friction, McIntyre&ndash;Woodhouse's friction-table
formulation. Playable interactive bowed string with bow force, velocity,
position, and pitch controls; Web-Audio listen.

### 8 &middot; Wind Instruments
The reed table as pressure-controlled nonlinear valve; cylindrical-bore
odd-harmonic series. Interactive clarinet with breath, embouchure, and
pitch controls.

### 9 &middot; Finite-Difference Time Domain (FDTD)
1-D leap-frog stencil and the "magic time step"; 2-D five-point stencil
and the Courant condition $\lambda \le 1/\sqrt{2}$. Interactive 2-D square
membrane &mdash; click anywhere to excite, watch modes develop, listen to the
virtual-mic output.

### 10 &middot; Modal Synthesis
Objects as sums of damped biquad resonators. Presets for marimba bar, metal
plate, church bell, glass tube; live inharmonicity and decay-scale
controls.

### 11 &middot; Commuted Synthesis for Piano
Smith &amp; Van Duyne's 1995 linearity-and-commutativity insight. Tiny
twelve-note piano: click any ivory key and hear a full commuted
hammer&ndash;soundboard&ndash;string cascade.

### 12 &middot; Artificial Reverberation via Waveguide Networks
Schroeder's 1962 parametric reverberator; Jot &amp; Chaigne's Feedback
Delay Network; the energy-preserving unitary feedback matrix. Small
4-line FDN with Hadamard feedback, interactive RT60 / colour / size,
impulse and snare demos.

### 13 &middot; Legacy and Continuing Impact
Yamaha VL series, Pianoteq, Modalys, DDSP and differentiable physical
models. Full bibliography and cross-links to the sibling guides.

---

## Technical Details

* **Zero dependencies.** No npm, no bundler, no external libraries. All
  rendering uses the HTML Canvas API. Audio uses the Web Audio API. Math
  typesetting uses KaTeX via jsdelivr &mdash; the only third-party asset.
* **All physics computed in real time.** Every waveguide, friction table,
  reed table, FDTD stencil, modal bank, convolution, and scattering
  junction is calculated live in the browser.
* **Audio playback.** Every instrument can be listened to via the Web Audio
  API &mdash; synthesised on demand, not pre-recorded.
* **Responsive.** Canvases scale with DPR for sharp rendering on
  Retina/HiDPI displays.
* **Single file.** Everything lives in `index.html`.

### What's computed where

| Visualisation | Algorithm | Notes |
|---|---|---|
| Hero animation | Two travelling-wave arrays with fixed-end reflection | D'Alembert $y=y^{+}+y^{-}$ |
| Ch 2 timeline | Concentric orbits, one per milestone | Colour-coded by paradigm |
| Ch 3 bouncing lump | Two Float32 arrays $y^{+}, y^{-}$ with fixed/free BC | Live + audio readout at bridge |
| Ch 4 waveguide pluck | Two delay lines, reflection lowpass, pick-position comb | Full Web Audio playback |
| Ch 5 Karplus&ndash;Strong | Single delay line with one-zero averaging filter | Noise / impulse / rough excitation |
| Ch 6 scattering junction | Two-port Fresnel scattering in admittance form | $r, t$ coefficients displayed live |
| Ch 7 bowed string | Two delay lines + friction-table nonlinearity | Stick&ndash;slip $\mu(v_{\text{rel}})$ |
| Ch 8 clarinet | Cylindrical bore waveguide + reed table | Pressure-controlled valve with closure |
| Ch 9 FDTD 2-D membrane | Five-point leap-frog stencil | Click-to-excite; virtual mic |
| Ch 10 modal synthesis | Biquad resonator bank | Presets for bar/plate/bell/tube |
| Ch 11 commuted piano | Hammer * board IR * string waveguide | Pre-convolved excitation |
| Ch 12 FDN reverb | 4 delay lines, Hadamard feedback, per-line lowpass | Unitary feedback matrix |

---

## Key References

1. Helmholtz, H. von (1862). *Die Lehre von den Tonempfindungen.* Braunschweig: Vieweg.
2. Raman, C. V. (1918). *On the Mechanical Theory of the Vibrations of Bowed Strings.* Bulletin of the Indian Association for the Cultivation of Science, 15, 1&ndash;158.
3. Hiller, L. &amp; Ruiz, P. (1971). *Synthesizing Musical Sounds by Solving the Wave Equation for Vibrating Objects.* JAES 19(6,7).
4. McIntyre, M. E. &amp; Woodhouse, J. (1979). *On the fundamentals of bowed-string dynamics.* Acustica 43, 93&ndash;108.
5. Karplus, K. &amp; Strong, A. (1983). *Digital Synthesis of Plucked-String and Drum Timbres.* Computer Music Journal 7(2), 43&ndash;55.
6. Jaffe, D. A. &amp; Smith, J. O. (1983). *Extensions of the Karplus&ndash;Strong Plucked-String Algorithm.* Computer Music Journal 7(2), 56&ndash;69.
7. Smith, J. O. (1987). *Music Applications of Digital Waveguides.* CCRMA Technical Report STAN-M-39.
8. Smith, J. O. (1992). *Physical Modeling Using Digital Waveguides.* Computer Music Journal 16(4), 74&ndash;91.
9. Cadoz, C., Luciani, A. &amp; Florens, J.-L. (1984). *Responsive Input Devices and Sound Synthesis by Simulation of Instrumental Mechanisms: The Cordis System.* Computer Music Journal 8(3), 60&ndash;73.
10. Adrien, J.-M. (1991). *The Missing Link: Modal Synthesis.* In De Poli et al., eds., *Representations of Musical Signals*, MIT Press, 269&ndash;297.
11. Smith, J. O. &amp; Van Duyne, S. A. (1995). *Commuted Piano Synthesis.* Proc. ICMC, 319&ndash;326.
12. Smith, J. O. (2010). *Physical Audio Signal Processing.* W3K Publishing. [ccrma.stanford.edu/~jos/pasp](https://ccrma.stanford.edu/~jos/pasp/)
13. Jot, J.-M. &amp; Chaigne, A. (1991). *Digital Delay Networks for Designing Artificial Reverberators.* Proc. AES 90th Convention.
14. Schroeder, M. R. (1962). *Natural Sounding Artificial Reverberation.* JAES 10(3), 219&ndash;223.
15. Kelly, J. L. &amp; Lochbaum, C. C. (1962). *Speech Synthesis.* Proc. 4th ICA, G42, 1&ndash;4.
16. Bilbao, S. (2009). *Numerical Sound Synthesis: Finite Difference Schemes and Simulation in Musical Acoustics.* Wiley.
17. Serafin, S. (2004). *The Sound of Friction: Real-Time Models, Playability and Musical Applications.* Ph.D. thesis, Stanford University.
18. Engel, J., Hantrakul, L., Gu, C. &amp; Roberts, A. (2020). *DDSP: Differentiable Digital Signal Processing.* ICLR 2020.

---

## Related Guides

* [Synth &mdash; Physical Modelling](https://github.com/BrendanJamesLynskey/Synth_Physical_Modelling) &mdash; a practitioner's walk through the same techniques.
* [Room Acoustics &amp; Reverb](https://github.com/BrendanJamesLynskey/Room_Acoustics_Reverb) &mdash; geometric and parametric reverb.
* [DDSP &mdash; Differentiable DSP](https://github.com/BrendanJamesLynskey/DDSP_Differentiable_DSP) &mdash; neural physical models.
* [Spatial Audio &amp; Ambisonics](https://github.com/BrendanJamesLynskey/Spatial_Audio_Ambisonics) &mdash; 3-D sound fields.
* [STFT for Sound](https://github.com/BrendanJamesLynskey/STFT_for_Sound) &mdash; spectrograms and phase vocoders.
* [Companion: *Mathematics of the DFT*](https://github.com/BrendanJamesLynskey/Companion_JOS_Mathematics_of_the_DFT)
* [Companion: *Introduction to Digital Filters*](https://github.com/BrendanJamesLynskey/Companion_JOS_Introduction_to_Digital_Filters)
* [Companion: *Spectral Audio Signal Processing*](https://github.com/BrendanJamesLynskey/Companion_JOS_Spectral_Audio_Signal_Processing)
* [Companion: *Audio Signal Processing in Faust*](https://github.com/BrendanJamesLynskey/Companion_JOS_Audio_Signal_Processing_in_Faust)

---

## License

MIT &mdash; use it however you like. Attribution appreciated but not required.
