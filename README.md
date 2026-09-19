### IIR-FILTER-DESIGN

### EXP 3 B: DESIGN OF LOW PASS CHEBYSHEV IIR FILTER USING BILINEAR TRANSFORMATION

### AIM: 
To a design of low pass Chebyshev IIR filter using Bilinear Transformation.

### APPARATUS REQUIRED: 
PC installed with SCILAB. 

### PROGRAM: 
```
clc;
close;
wp=input('Enter the pass band frequency (Radians) = ');
ws=input('Enter the stop band frequency (Radians) = ');
alphap=input('Enter the pass band attenuation (dB) = ');
alphas=input('Enter the stop band attenuation (dB) = ');
T=input('Enter the value of sampling time = ');
omegap=(2/T)*tan(wp/2);
disp(omegap,'omegap = ');
omegas=(2/T)*tan(ws/2);
disp(omegas,'omegas = ');
N=acosh(sqrt(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1)))/(acosh(omegas/omegap));
disp(N,'N = ');
N=ceil(N);
disp(N,'Round off value of N = ');
omegac=omegap/(((10^(0.1*alphap))-1)^(1/(2*N)));
disp(omegac,'omegac = ');
Epsilon=sqrt((10^(0.1*alphap))-1);
disp(Epsilon,'Epsilon = ');
[pols,gn]=zpch1(N,Epsilon,omegap);
disp(gn,'Gain');
disp(pols,'Poles');
hs=poly(gn,'s','coeff')/real(poly(pols,'s'));
disp(hs,'Analog Low Pass Chebyshev Filter Transfer Function');
z=poly(0,'z');
Hz=horner(hs,(2/T)*((z-1)/(z+1)));
disp(Hz,'Digital LPF Transfer Function H(Z) = ');
HW=frmag(Hz,512);
w=0:%pi/511:%pi;
plot(w/%pi,abs(HW));
xlabel('Normalized Digital Frequency w');
ylabel('Magnitude');
title('Frequency Response of Chebyshev IIR LPF');
```

### CALCULATION:
<img width="899" height="1599" alt="WhatsApp Image 2026-09-19 at 08 27 55" src="https://github.com/user-attachments/assets/0946321f-64d5-4ff7-895c-0242502e215e" />
<img width="899" height="1599" alt="WhatsApp Image 2026-09-19 at 08 28 03" src="https://github.com/user-attachments/assets/e11ac4c2-166c-4276-8796-43ce2b0dc001" />
<img width="899" height="1599" alt="WhatsApp Image 2026-09-19 at 08 28 12" src="https://github.com/user-attachments/assets/21644c1b-5a62-4860-899b-bc9cba74919e" />
<img width="899" height="1599" alt="WhatsApp Image 2026-09-19 at 08 28 24" src="https://github.com/user-attachments/assets/94d2f227-5403-4ddf-b78b-f46a18dfe38c" />

### OUTPUT: 

<img width="707" height="552" alt="image" src="https://github.com/user-attachments/assets/1f5a10ab-83d3-4b17-b3e5-d14325e71f70" />

### RESULT: 
Thus design of Chebyshev Low pass IIR filter waveforms were plotted and output was
verified.
