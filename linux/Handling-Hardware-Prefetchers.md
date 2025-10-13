## Handling Hardware Prefetchers 

* OS: Ubuntu 24.04
* CPU: 13th Gen Intel(R) Core(TM) i5-13400

### Allow Writes to MSR

`echo 1 | sudo tee /sys/module/msr/parameters/allow_writes`

### To check if HW prefetchers are disabled

`sudo rdmsr -p 0 0x1A4`

-p 0 : For core 0 \
-a : For all

### To disable HW prefetchers:

`sudo wrmsr -p 0 0x1A4 0xF`

For enable: 0x0



