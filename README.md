# Design-of-First-Order-Sigma-Delta-A-D-Converter

## Table of Contents

- Abstract 
- Introduction
- Expected waveform
- Circuit implementation of PFD block 
- Circuit implementation of CP + LPF block
- Circuit implementation of VCO block
- Simulation Result
- Conclusion
- Author
- Acknowledgements
- References
## Abstract 
The paper presents an approach to study and simulate the first order Sigma-Delta Analog to Digital Converter on a 180um Technology with mixed signal approach. Sigma-Delta modulators (ΣΔMs) have now widely used for the interface implementation for analog/digital electronic systems implemented with CMOS technologies. Comparing with other varieties of analog-to-digital converters (ADCs), ΣΔMs cover the widest conversion region of the resolution-versus-bandwidth plane. These can be efficiently be used to digitize diverse types of signals having numerous applications which are widely used in our electronics and communication systems i.e. from high-resolution low-bandwidth data conversions for digital audio, sensor interfaces, and instrumentation, to ultra-low-power biomedical systems and medium-resolution broadband wireless communications.</br>

## Introduction

CMOS technology scaling has motivated the replacement
of analog components in signal-processing systems with
their digital counterparts for improved reliability, flexibility,
and process portability Analog to Digital Converters
(ADCs) are the most critical modules in modern voice band,
audio, communication and high-resolution precision
industrial measurement applications. The efficient
realization of ADC, with low power, smaller board size and
low cost allows benefits in all most all electronic products.
The present day scenario of separate ADC chip followed by
ASIC or FPGA approach for doing DSP has the following
limitations.</br>

Working:- Delta-sigma (ΔΣ; or sigma-delta, ΣΔ) modulation is a method for encoding analog signals into digital signals as found in an analog-to-digital converter (ADC). It is also used to convert high bit-count, low-frequency digital signals into lower bit-count, higher-frequency digital signals as part of the process to convert digital signals into analog as part of a digital-to-analog converter (DAC)</br>

## Reference Circuit Diagram

The fig. here represents the Model schematis that is to be implemented here.</br>

## Reference Waveform

## Circuit Implementation</br>
- Circuit implementation of op amp block</br>
- Sub circuit creation of op-am</br>
- Integrator block using LM 741</br>
- Differencial amplifier using LM741</br>
- D-FF Sub ckt cration (using verilog code)</br>
- Cascaded Block</br>
1-Bit ADC and 1-Bit DAC is being Instantiated (To improve the output Pre-defined op-amp LM741 is being instantiated)</br>

## Verilog implementaion of D-FlipFlop</br>
- Code used</br>
- Makerchip Display</br>

## Simulation Results and Observation</br>
- D-FF USING VERILOG on MAKERCHIP</br>
- Input and Output to the circuit</br>
- Final results for each block</br>
- After increaing the Frequency of the input</br>

## Observation and Calculation</br>
- It is being observed that for the Analog (sin) input to the block a bit stream output is being observed at the output </br>
- For Integrator circuit selection of R and C is being taken usinf these formula</br>

## Result
1-Bit Sigma-Delta ADC is being implemented on 180nm Technology using Ngspice Smulation Tool (It is an Open Source EDA developed by FOSSEE, IIT Bombay. It is used for electronic circuit simulation. It is made by the combination of two software namely NgSpice and KiCAD.)
</br>

## Author

Bishal Kumar Gupta, M.tech at Defence Institute of Advanced Technology-DRDO [in collaboration with NIELIT CALICUT] with specialization in VLSI and Embedded Systems, Department of Electronics Engineering.

## Acknowledgements



## References

