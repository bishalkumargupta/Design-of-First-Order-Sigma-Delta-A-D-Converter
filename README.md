# Design-of-First-Order-Sigma-Delta-A-D-Converter

## Table of Contents

- Abstract 
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
<p align="center">
<img src="https://user-images.githubusercontent.com/86653033/157710863-9af44ff6-366a-4f9a-b477-65410053102f.png">
</p>

## Reference Waveform
<p align="center">
  <img src="https://user-images.githubusercontent.com/86653033/157711191-9ecedd2b-4e6c-467b-aa66-4af4ffeca81e.png">
</p>


## Circuit Implementation</br>
- Circuit implementation of op amp block</br>
<p align="center">
  <img src="https://user-images.githubusercontent.com/86653033/157711842-89b099e1-b1c0-4cc9-bf94-b6b20cd8f896.png">
</p>

- Sub circuit creation of op-am</br>
<p align="center">
  <img src="https://user-images.githubusercontent.com/86653033/157712083-05ea8869-9d7d-4c5b-90fd-12ae8c081808.png">
</p>

- Integrator block using LM 741</br>
<p align="center">
  <img src="https://user-images.githubusercontent.com/86653033/157712359-2dbea07c-8bd5-4fd3-835f-b2f9de85d9cd.png">
</p>

- Differencial amplifier using LM741</br>
<p align="center">
  <img src="https://user-images.githubusercontent.com/86653033/157712591-6d52565d-9dd9-4f4f-be75-28373bc693fa.png">
</p>


- D-Latch Sub ckt cration (using verilog code)</br>
<p align="center">
  <img src="https://user-images.githubusercontent.com/86653033/157713268-887ed548-8f7e-4214-b213-795586f58e7e.png">
</p>

- Cascaded Block</br>
1-Bit ADC and 1-Bit DAC is being Instantiated (To improve the output Pre-defined op-amp LM741 is being instantiated)</br>
<p align="center">
  <img src="https://user-images.githubusercontent.com/86653033/157713467-b264cdf4-4e22-4bf5-8a60-b8586b0b9abe.png">
</p>

## Verilog implementaion of D-Latch</br>
- Code used</br>
module d_latch (  input d,           // 1-bit input pin for data  
                  input en,          // 1-bit input pin for enabling the latch  
                  input rstn,        // 1-bit input pin for active-low reset  
                  output reg q);     // 1-bit output pin for data output  
  
   // This always block is "always" triggered whenever en/rstn/d changes  
   // If reset is asserted, then the output will be zero   
   // Else as long as enable is high, output q follows input d  
  
   always @ (en or rstn or d)  
      if (!rstn)  
         q <= 0;  
      else  
         if (en)  
            q <= d;  
endmodule   
- Makerchip Display</br>

\TLV_version 1d: tl-x.org
\SV
/* verilator lint_off UNUSED*/  /* verilator lint_off DECLFILENAME*/  /* verilator lint_off BLKSEQ*/  /* verilator lint_off WIDTH*/  /* verilator lint_off SELRANGE*/  /* verilator lint_off PINCONNECTEMPTY*/  /* verilator lint_off DEFPARAM*/  /* verilator lint_off IMPLICIT*/  /* verilator lint_off COMBDLY*/  /* verilator lint_off SYNCASYNCNET*/  /* verilator lint_off UNOPTFLAT */  /* verilator lint_off UNSIGNED*/  /* verilator lint_off CASEINCOMPLETE*/  /* verilator lint_off UNDRIVEN*/  /* verilator lint_off VARHIDDEN*/  /* verilator lint_off CASEX*/  /* verilator lint_off CASEOVERLAP*/  /* verilator lint_off PINMISSING*/ /* verilator lint_off BLKANDNBLK*/  /* verilator lint_off MULTIDRIVEN*/  /* verilator lint_off ASSIGNDLY*/  /* verilator lint_off MODDUP*/  /* verilator lint_off STMTDLY*/  /* verilator lint_off LITENDIAN*/  /* verilator lint_off INITIALDLY*/    

//Your Verilog/System Verilog Code Starts Here:
module dlatch (  input d,           // 1-bit input pin for data  
                  input en,          // 1-bit input pin for enabling the latch  
                  input rstn,        // 1-bit input pin for active-low reset  
                  output reg q);     // 1-bit output pin for data output  
  
   // This always block is "always" triggered whenever en/rstn/d changes  
   // If reset is asserted, then the output will be zero   
   // Else as long as enable is high, output q follows input d  
  
   always @ (en or rstn or d)  
      if (!rstn)  
         q <= 0;  
      else  
         if (en)  
            q <= d;  
endmodule  

//Top Module Code Starts here:
	module top(input logic clk, input logic reset, input logic [31:0] cyc_cnt, output logic passed, output logic failed);
		logic  d;//input
		logic  en;//input
		logic  rstn;//input
		logic  q;//output
//The $random() can be replaced if user wants to assign values
		assign d = 20'b01001010011011001100;
		assign en = 20'b01010101010101010101;
		assign rstn = 20'b10000000000000000000;
		dlatch dlatch(.d(d), .en(en), .rstn(rstn), .q(q));
	
\TLV
//Add \TLV here if desired                                     
\SV
endmodule


## Simulation Results and Observation</br>
- D-FF USING VERILOG on MAKERCHIP</br>
<p align="center">
  <img src="https://user-images.githubusercontent.com/86653033/157718393-8cb21aee-2a7e-4536-be97-c5ea37c6bc4c.png">
</p>


- Input and Output to the circuit</br>
<p align="center">
  <img src="https://user-images.githubusercontent.com/86653033/157720901-54ce0114-dd87-4dae-890b-df5670c23600.png">
</p>


- Final results for each block</br>
<p align="center">
  <img src="https://user-images.githubusercontent.com/86653033/157721412-52e136e4-bd8e-47f9-83fa-abc23b96193a.png">
</p></br>
- Differentiator output
<p align="center">
  <img src="https://user-images.githubusercontent.com/86653033/157721856-169eaffd-7316-4779-b78b-91d532dde979.png">
</p></br>

- Comperator output

<p align="center">
  <img src="">
</p></br>




- After increaing the Frequency of the input</br>
<p align="center">
  <img src="">
</p></br>


## Observation and Calculation</br>
- It is being observed that for the Analog (sin) input to the block a bit stream output is being observed at the output </br>
- For Integrator circuit selection of R and C is being taken usinf these formula</br>

## Result
1-Bit Sigma-Delta ADC is being implemented on 180nm Technology using Ngspice Smulation Tool (It is an Open Source EDA developed by FOSSEE, IIT Bombay. It is used for electronic circuit simulation. It is made by the combination of two software namely NgSpice and KiCAD.)
</br>

## Author

Bishal Kumar Gupta, M.tech at Defence Institute of Advanced Technology-DRDO [in collaboration with NIELIT CALICUT] with specialization in VLSI and Embedded Systems, Department of Electronics Engineering.

## Acknowledgements
- Kunal Ghosh (Co-Founder, VLSI System Design Pvt. Ltd.)

- FOSSEE, IIT Bombay

- Steve Hoover (Founder, Redwood EDA)

- Sumanto Kar (eSim Team, FOSSEE, IIT Bombay)


## References
[1] H. Dadhich, V. Maurya, K. Verma and S. Jaiswal, "Design and analysis of different type of charge pump using CMOS technology," 2016 International Conference on Advances in Computing, Communications and Informatics (ICACCI), 2016, pp. 294-298, doi: 10.1109/ICACCI.2016.7732062.
[2] Design of CMOS Integrator Circuit for Sigma Delta ADC for Aerospace Application
[3] M. L. Ya et al., "Design and analysis of a first-order sigma-delta analog-to-digital converter for MEMS resistive sensor," 2010 IEEE International Conference on Semiconductor Electronics (ICSE2010), 2010, pp. 297-300, doi: 10.1109/SMELEC.2010.5549366.
[4] https://www.beis.de/Elektronik/DeltaSigma/DeltaSigma.html
