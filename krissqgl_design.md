\# Jasueng Ku  
\# kirssqgl is a python package for Quantum Gate Languates to build pulse sequences
\# Inspired by BBN QGL
\# Below I outline things that I'd like to include in the package

# General rules for design 
- Design for interface.
- How to configure experiments
- Make it modular
- Make it easy for scripting
- Make it easy to extend
- Obey SOLID principle as much as possible
    - Single responsibility principle
    - Open-closed principle: open for  extension, close for modification
    - Liskov substitution principle
    - Interface segregation principle
    - Dependency inversion principle
 - Obey PEP8
 - Make a good documentation
 
# krissQqgl: kriss Quantum Gate Language package
- Act as an interface layer between python gate layer and physical hardware's API to define pulse sequences
     (no need to know each AWG's language/API, for example, `seq = [X(q1), Y90(q1)])` instead of `wavejoin(w1, w2)`.)
- Use gates in most cases (without knowing how to create them in reality) in defining pulse seqs.
- Would this be practical for ZI and QM?

## Modules:
- Channels: LogicalChannel, Qubit, CR, Readout, Marker
  - Qubit:
    - attribute:SSB, pulse_params(pulse_shape, length, pi2amp, piamp, drag,..), physical_channel
    - method: set_physical_channel()
  - Readout: SSB, pulse_params(pulse_shape, length, amp), physical_channel, set_physical_channel()
  - CR: controlQ, targetQ, SSB, length, amp, phase

- Pulse_primatives (Utheta, Xtheta, Ytheta, X90, Y90, Z, CR, echoCR, rotaryCR, ...)
- Pulsequencer: define pulse sequences
- Pulse_shapes: define required pulse params for each pulse
- Pulsecollection (collections of functions or classes) 
    - characterization: spec, Rabi, Ramsey, Echo, T1, decoupling..
    - calibration: RabiAmpCal, PiCal, Pi2Cal, DragCal, CR ... 
    - verification: RB, QST, QPT, HamiltonianTomo, GST,...
    - PulseSeqPlotter
