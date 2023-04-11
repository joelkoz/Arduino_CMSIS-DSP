# Arduino_CMSIS-DSP

This is a version of the ARM CMSIS-DSP library re-arranged for use in PlatformIO or other Arduino style development environments.
Code here is as of CMSIS-DSP version 1.10.0

The original code can be found [here](https://github.com/ARM-software/CMSIS-DSP).

# Re-creating from scratch
This library was built using the following steps:

1. Change to a directory where you store library files and workspaces

2. Check out CMCSIS-DSP from ARM's GitHub:
```
   git clone https://github.com/ARM-software/CMSIS-DSP.git
```

3. Check out the "convert to Arduino lib" code from GitHub:
```
   git clone https://github.com/arduino-libraries/Arduino_CMSIS-DSP.git
```

4. Change to Arduino lib subdir:
```
   cd Arduino_CMSIS-DSP
```

5. Break the link to GitHub from the Arduino lib:
```
   rm -rf .git
```

6. Edit the script `create_lib` and change line 4 from
```
cp -r ${CMSIS_PATH}/CMSIS_5/CMSIS/DSP/* .
```
to:
```
cp -r ../CMSIS-DSP/* .
```


7. Run the script to make the Arduino Source version of CMSIS-DSP:
```
   ./create_lib
```

8. Modify `libraries.properies` and:

   a. Change 'version' to match that of the version found in the comments of `Include/arm_math.h`:
```
      version=1.10.0
```
   b. add 'nrf52480' to end of 'architectures' list:
```   
      architectures=mbed,mbed_nano,mbed_portenta,mbed_rp2040,mbed_edge,nrf52840
```

Step 8a is for completeness. Not sure if Step #8b is necessary or not

