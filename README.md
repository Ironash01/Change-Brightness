# Change-Brightness-Terminal 
Modifies brightness manually. For laptops that for some reason uses nvidia_wmi_ec_backlight instead of intel_backlight.
Variables to modify yourself!

**Please backup your files manually beforehand!! the files needed are "_brightness_" and "_max_brightness_"** 
These files should be inside
```
/sys/class/backlight/YOURBACKLIGHTHERE/
```

This two variables below will specify your backlight directory.
 ```
directoryBacklight=""
directoryMaxBacklight=""
```
To find your backlight directory:
```
ls /sys/class/backlight
```

For Intel cards
```
directoryBacklight="/sys/class/backlight/intel_backlight/brightness"
directoryMaxBacklight="/sys/class/backlight/intel_backlight/max_brightness"
```
**If you have a different card or backlight directory please submit an issue so I can add it here in the readme for others to see**

This modifies the minimum value for your brightness, simply put if brightnessInput < brightnessMin the program exits.
**The values here are percentage based! Modify the number after the *
Note that going below 10 percent is not recommended.**
```
brightnessMin=$(cat $directoryMaxBacklight)
brightnessMin=$(echo "scale=2; $brightnessMin * 0.10" | bc)
brightnessMin=${brightnessMin%.*}
```
for exact value:
```
#brightnessMin=$(cat $directoryMaxBacklight)
#brightnessMin=$(echo "scale=2; $brightnessMin * 0.10" | bc)
brightnessMin=
```
This modifies maximum value for your brightness. Same principles as the min one.
Again modify the multiplier as this is percentage based. Comment out first two lines for exact value.
```
brightnessMax=$(cat $directoryMaxBacklight)
brightnessMax=$(echo "scale=2; $brightnessMax * 0.60" | bc)
brightnessMax=${brightnessMax%.*}
```
Exact value:
```
#brightnessMax=$(cat $directoryMaxBacklight)
#brightnessMax=$(echo "scale=2; $brightnessMax * 0.60" | bc)
brightnessMax=
```
To call the script
```
cd "/path/to/script"
bash ./scriptname
```

Make the script executable and run
```
cd "/path/to/script"
chmod +x scriptname
./scriptname
```

Call the script anywhere
```
mv scipt ~/bin/
```
If directory does not exist, create it
```
mkdir ~/bin
```
Restart and check path
```
echo $PATH
```
Now you can call the cbt anywhere
```
cbt #Should run my script now
```
