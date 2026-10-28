# Lab3

Q2: 
Accelerometer : 0011001, r/w bit : 0011001b - 0x19

Magnetometer :  0011110, r/w bit : 0011110b - 0x1E
 
What is the sub-address (SUB), and how does it differ from the I2C address?
An internal chip/a register address inside a device, it tells the device which intneral register to read/write to. Whereas the I2C address is the 7-bit address of the device itself, it tells the bus which device it should listen to. 

Q3: 
CTRL_REG1_A Register address: 0x20

ODR[3:0] - data rate selection, default: 0000
Zen, Yen, Xen - enable bits: 111
Lpen: low-power mode enable, deafult: 0 (normal mode)
pg. 36 : Write CTRL_REG1_A = 57h // Accel = 100 Hz (normal mode)
What should be written: 0101 0111 - 0x57

Q4: 

OUT_X_L_A : 010 1000 
OUT_X_H_A : 010 1001
OUT_Y_L_A : 010 1010
OUT_Y_H_A : 010 1011
OUT_Z_L_A : 010 1100
OUT_Z_H_A : 010 1101

