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


part 5 - answer: 
HAL_I2C_Mem_Read(&hi2c1, 0x19 << 1, 0x28, I2C_MEMADD_SIZE_8BIT, &X_LA, 1, HAL_MAX_DELAY);

changed to: HAL_I2C_Mem_Read(&hi2c1, 0x19 << 1, addr, I2C_MEMADD_SIZE_8BIT, start, 6 , HAL_MAX_DELAY);

- I changed the 0x28, which was the X -axis register address ( and veries per axis, per LA or HA), to the X-axis register address (start) or'ed with a mask to change the MSB to 1 in order to enable the auto increment setting mentioned in the datasheet. 
- then I changed the 1 byte to 6 since there was 6 different read functions (each for a different axis LA/HA), this will allow us to move through all the registers (0x28 to 0x2D)
- Lastly, I initialized an array of size 6, this way I could store each memread into the array and call it so I could build X, Y, and, Z after the increment is finished. Everything else pretty much stayed the same 


