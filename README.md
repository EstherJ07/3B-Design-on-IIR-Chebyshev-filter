# IIR-FILTER-DESIGN

# EXP 3 B: DESIGN OF LOW PASS CHEBYSHEV IIR FILTER USING BILINEAR TRANSFORMATION

# AIM: 

# To a design of low pass Chebyshev IIR filter using Bilinear Transformation.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```
clc;
close;
wp=input('Enter the pass band frequency (Radians)=');
ws=input('Enter the stop band frequency (Radians)=');
alphap=input('Enter the pass band attenuation (dB)=');
alphas=input('Enter the stop band attenuation (dB)=');
T=input('Enter the Value Of Sampling Time=');
omegap=(2/T)*tan(wp/2);
disp(omegap,'omegap=');
omegas=(2/T)*tan(ws/2);
disp(omegas,'omegas=');
N=acosh(sqrt(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1)))/(acosh(omegas/omegap));
disp(N,'N=');
N=ceil(N);
disp(N,'Round off value of N=');
omegac=omegap/(((10^(0.1*alphap))-1)^(1/(2*N)));
disp(omegac,'omegac=');
Epsilon=sqrt((10^(0.1*alphap))-1);
disp(Epsilon,'Epsilon=');
[pols,gn]=zpch1(N,Epsilon,omegap);
disp(gn,'Gain');
disp(pols,'Pols');
hs=poly(gn,'s','coeff')/real(poly(pols,'s'));
disp(hs,'Analog Low pass chebyshev filtertransfer function');
z=poly(0,'z');
Hz=horner(hs,(2/T)*((z-1)/(z+1)))
disp(Hz,'Digital LPF Transfor function H(Z)=');
HW=frmag(Hz,512);
w=0:%pi/511:%pi;
plot(w/%pi,abs(HW));
xlabel('Normalized Digital Frequency w');
ylabel('Magnitude');
title('Frequency Response of Chebyshev IIR LPF');
```
**CALCULATION**
<img width="932" height="1454" alt="image" src="https://github.com/user-attachments/assets/0b3a5f35-9926-45ee-a86c-f953479ded24" />
<img width="803" height="1454" alt="image" src="https://github.com/user-attachments/assets/cc4d5c08-2852-4c67-a00b-d2536541d337" />
<img width="940" height="1380" alt="image" src="https://github.com/user-attachments/assets/bdadf648-249b-4e33-8f4f-3c79a81b0884" />
<img width="940" height="283" alt="image" src="https://github.com/user-attachments/assets/93bea5e6-27a9-4be7-bcf9-a4acff8cb763" />




# OUTPUT: 
<img width="1369" height="828" alt="image" src="https://github.com/user-attachments/assets/93acd0c1-6e94-4ee6-911a-ab26b7929afb" />

# RESULT: 
Thus design of Chebyshev Low pass IIR filter waveforms were plotted and output was
verified.
