# Raspberry__HAL_GPIO_addressing
The proper way to address HAL_GPIO with LinuxCNC or Machinekit HAL loadrt dir and exclude parameters
This information was hard to come by for some reason. 

Basically you target the GPIO number in your dir and exclude parameters of the loadrt command. 
From the Source:

// Raspberry2:
static unsigned char rpi2_gpios[] = {2, 3, 4, 5,   6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27 };
static unsigned char rpi2_pins[] =  {3, 5, 7, 29, 31, 26, 24, 21, 19, 23, 32, 33,  8, 10, 36, 11, 12, 35, 38, 40, 15, 16, 18, 22, 37, 13 };

What is targeted here is a mask value that goes up in value of 2, for example:

// Raspberry2:
 rpi2_gpio 
 2, 3, 4, 5,   6,  7,  8,  9,   10,   11,   12,   13,   14,   15,    16,     17,   18,     19,     20,     21,      22,      23,      24,      25,      26,        27 
mask:
 1, 2, 4, 8,  16, 32, 64, 128, 256,  512, 1024, 2048, 4096, 8192, 16384, 32768, 65536, 131072, 262144, 524288, 1048576, 2097152, 4194034,  8388608, 16777216, 33554432
 
 The values are ANDed together. 
 
 More to come as the original notes are found
