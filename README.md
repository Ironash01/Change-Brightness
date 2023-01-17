# Change-Brightness
Modifies intel brightness manually. For laptops that for some reason uses nvidia_wmi_ec_backlight instead of intel_backlight.
Variables to modify yourself!

This two variables below will specify your backlight directory.
 
directoryBacklight=""
directoryMaxBacklight=""

To find your backlight directory:
ls /sys/class/backlight

For Intel cards
directoryBacklight="/sys/class/backlight/intel_backlight/brightness"
directoryMaxBacklight="/sys/class/backlight/intel_backlight/max_brightness"

This modifies the minimum value for your brightness, simply put if brightnessInput < brightnessMin the program exits.
The values here are percentage based!Modify the number after the * 
Note that going below 10 percent is not recommended.

brightnessMin=$(cat $directoryMaxBacklight)
brightnessMin=$(echo "scale=2; $brightnessMin * 0.10" | bc)
brightnessMin=${brightnessMin%.*}

for exact value:

#brightnessMin=$(cat $directoryMaxBacklight)
#brightnessMin=$(echo "scale=2; $brightnessMin * 0.10" | bc)
brightnessMin=

This modifies maximum value for your brightness. Same principles as the min one.
Again modify the multiplier as this is percentage based. Comment out first two lines for exact value.

brightnessMax=$(cat $directoryMaxBacklight)
brightnessMax=$(echo "scale=2; $brightnessMax * 0.60" | bc)
brightnessMax=${brightnessMax%.*}

Exact:

#brightnessMax=$(cat $directoryMaxBacklight)
#brightnessMax=$(echo "scale=2; $brightnessMax * 0.60" | bc)
brightnessMax=

To run this script cd into dir and run bash "insert script name here"
Watch how to use here: https://youtu.be/sZJW7ZYMIfs
Not a channel plug, just wanted to demonstrate it.
