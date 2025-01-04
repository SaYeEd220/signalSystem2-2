%Exponential growing or damping funtion (sin or cos)
A= 200;
a = -3; % for damping signal
f =20;
fs= 100;
T= 1/fs;
t = -1:T:1;
phi = 2;

% exponential damping cosin signal
x_original = A *exp(a * t) .* cos(2*pi*f*t + phi);

% reflected signal 
x_reflected = A * exp(a *(-t)) .* cos(2*pi*f*(-t) + phi);


%even part
x_even = (x_original + x_reflected)/2;

%odd part
x_odd = (x_original - x_reflected)/2;

% Reconstructiin Signal
x_reconstructed = (x_even + x_odd);

%figure the different sigs
figure;

subplot(3,2,1);
plot(t,x_original, 'b*-');
title('Original Exponential signal');
xlabel('Time(s)');
ylabel('Amplitude');
grid on;

subplot(3,2,2);
plot(t,x_reflected, 'k*-');
title('Reflected Signal');
xlabel('Time(s)');
ylabel('Amplitude');
grid on;

subplot(3,2,3);
plot(t,x_even, 'g*-');
title('Even Part');
xlabel('Time(s)');
ylabel('Amplitude');
grid on;

subplot(3,2,4);
plot(t,x_odd, 'm*-');
title('Odd Part');
xlabel('Time(s)');
ylabel('Amplitude');
grid on;

subplot(3,2,5);
plot(t,x_reconstructed, 'k*-');
title('Reconstructed Signal');
xlabel('Time(s)');
ylabel('Amplitude');
grid on;

