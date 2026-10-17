# Radar Signal - BPSK-BARKER13 Radar Signal Simulation [with MATLAB Code]

\n        \n  
In the formula, u(t) represents the complex envelope of the signal, which can be expressed as:
\n        \n  
In which φ(t) is the phase modulation function. In two-phase coding, φ(t) can take values of 0 or π, and can be represented by a phase sequence or a binary sequence. Therefore, the two-phase coding signal can be expressed as:
\n        \n  
The aforementioned binary sequence is the BARKER13 code sequence.
MATLABCode%finished:2020-10-17 20:42:18\n%created by xxx\nclear all; \nclose all;\nclc;\n% function Bpsk_barker13=barker13(fc,fs,Baud)\n% Requirement: Signal pulse width 0.65us, which is equivalent to Baud = 2e7\n% The pulse width = the number of code elements * the width of each code element\ng=[1,1,1,1,1,0,0,1,1,0,1,0,1];%13BCD code\nfc=2e8;                  %Carrier Frequency\nfs=2e9;                  % Sampling rate\nBaud=2e7;                  % Baud rate\n​\nt=0:1/fs:(fs/Baud-1)/fs;               % This step is crucial, as it determines whether the carrier sampling points and the symbol sampling points have the same length.\n​\n% Generate sequence\ncp=[];\nmod1=[];\nfor n=1:length(g)\n    if g(n)==0\n        A=zeros(1,fs/Baud);\n    else \n        A=ones(1,fs/Baud);\n    end\n    c=sin(2*pi*fc*t);\n    cp=[cp A];%code sequence generated\n    mod1=[mod1 c];\nend\ncm=[];\nmod=[];\nsubplot(311);plot(cp);\n%% Inverse sin according to the sequence\nfor n=1:length(g)\n    if g(n)==0\n        B=ones(1,fs/Baud);     % Each value is 100 points\n       c=sin(2*pi*fc*t);         %Carrier signal\n    else \n        B=ones(1,fs/Baud);\n        c=sin(2*pi*fc*t+pi);     %Carrier signal\n    end\n    cm=[cm B];              %s(t) Binary code width 100\n    mod=[mod c];          %A carrier signal of equal length with s(t)\nend\nBpsk_barker13=cm.*mod;\nsubplot(312);plot(Bpsk_barker13);\n​\ny=fft(Bpsk_barker13);\nf = (0:length(y)-1)*fs/length(y);\nn = length(Bpsk_barker13);\nfshift = (-n/2:n/2-1)*(fs/n);\nyshift = fftshift(y);\nsubplot(313);plot(fshift,(abs(yshift)));\n​\n​\n\n  
MATLAB simulation results: 1. Bark code sequence and generation of BSPK-BARKER13 signal waveforms
\n        \n  
2. Time-frequency diagram
\n        \n  

## Images

![[Radar Signal]BPSK-BARKER13 Radar Signal Simulation [with MATLAB Code]](01.png)
![[Radar Signal]BPSK-BARKER13 Radar Signal Simulation [with MATLAB Code]](02.png)
![[Radar Signal]BPSK-BARKER13 Radar Signal Simulation [with MATLAB Code]](03.png)
![[Radar Signal]BPSK-BARKER13 Radar Signal Simulation [with MATLAB Code]](04.png)
![[Radar Signal]BPSK-BARKER13 Radar Signal Simulation [with MATLAB Code]](05.png)

<!-- PAYMENT_BLOCK -->

## Get this dataset

- Payment link (Stripe): [Buy now](https://buy.stripe.com/3cs8yP7sY87d0vu9AB)
- Payment QR code: ![Payment QR code](pay.png)

<!-- /PAYMENT_BLOCK -->
