# CGM
This section allows you to choose your glucose data source. Most options are self explanatory.  For more information on compatible CGMs, please see the following: [link](../../intro/)

CGM selection includes the following:
Nightscout
xDrip
Dexcom G5
Dexcom G6
Dexcom G7
Glucose Simulator
Libre Transmitter
Glucose Direct
Medtronic Enlite

# Nightscout
While using Nightscout as a cgm is an option, it should be avoided if possible beacuse it will not keep iAPS running in the background like other cgm options.

# xDrip (xDrip4iOS)
To use xDrip4iOS as a cgm source, you must build it yourself with the same Apple Developer account you used to build your iAPS app. You cannot use Shuggah or a version distributed by someone else's TestFlight. Please see the following for instructions on how to build xDrip4iOS yourself: [link](../../../operate/build.html#xdrip4ios-or-glucose-direct-as-cgm-source)

# Dexcom G5/G6
If you are using a Dexcom G5 or G6 sensor, tap Configuration CGM to enter your transmitter's 6-digit ID. Dexcom Share Credentials is not necissary. When you switch transmitters, you must delete your current transmitter from iAPS by tapping Configuration CGM, srolling down, and tapping Delete CGM. Once you do this, you can add the new transmitter with it's Transmitter ID.

# Glucose Simulator
This option should only be used when testing the app and not using it to manage a live person (or animal).

# Glucose Direct
To use Glucose Direct as a cgm source, you must build it yourself with the same Apple Developer account you used to build your iAPS app. You cannot use a version distributed by someone else's TestFlight.
