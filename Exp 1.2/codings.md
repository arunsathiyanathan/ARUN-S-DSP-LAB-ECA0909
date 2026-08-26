clc; clear
Fs=10000; Fp=3000; Fst=2000;
[N,Wn]=buttord(Fp/(Fs/2),Fst/(Fs/2),1,60);
[b,a]=butter(N,Wn,'high');
freqz(b,a)
figure
[h,n]=impz(b,a,50);
stem(n,h), grid on
title('Impulse Response')
figure
stepz(b,a)
title('Step Response')
figure
grpdelay(b,a)
title('Group Delay')
figure
zplane(b,a)
title('Pole-Zero Plot')
fprintf('Minimum Filter Order (N) = %d\n',N);
fprintf('Cutoff Frequency (Wn) = %.4f\n',Wn);