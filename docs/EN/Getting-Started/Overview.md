# Overview
iAPS (formerly FreeAPS X (FAX)) is an artificial pancreas system that is based on the [OpenAPS](https://openaps.readthedocs.io/en/latest) (oref1) algorithm that runs on an iPhone (iOS 15.1 or newer). This is a completely different algorithm than the algorithm used by Loop (and the FreeAPS fork of Loop).

## What is the state of FAX?

The initial implementation of FAX, by Ivan Valkou, was halted in spring 2022. That branch is stable and still in use, but not all features listed below are available in his [repository](https://github.com/ivalkou/freeaps#readme). For example, there is no DASH support or G7 support.

You should not attempt to use any version of iAPS unless you have a clear understanding of how DIY artificial pancreas systems work, are comfortable with the potential need to rebuild. You should be willing and able to provide detailed troubleshooting information to the developers when you have a problem.

## iAPS Code Repository
- [iAPS GitHub](https://github.com/Artificial-Pancreas/iAPS)
- You should join the [iAPS Discord](https://discord.gg/32VCtN3tMF) channel to follow along with updates.

For those coming to iAPS from Loop:
- The quick cancel of a bolus in the iAPS app is similar to Loop – but you must tap on the square icon in the middle of the bolus progress icon
- iAPS will update the IOB based on actual delivery from the interrupted bolus, but this may not show up until the next CGM reading is detected.
- In other words, do not panic when the IOB shows the full delivery of the interrupted bolus for the next 5 minutes.

# Units
Before entering any values into iAPS, select your units. The default is mmol/l.
- Tap Settings, Preferences and adjust Glucose Units to mg/dl if that is your system of units
- Please read the Initial Preferences and Advanced Preferences before modifying any other preferences from the defaults

## Hardware
### Computer
- For Xcode Build: Access to a Mac (or Virtual Machine) – Monterey (macOS 12.5) or higher with Xcode 14.1 or higher
- For GitHub Build (on a browser with any computer – no Mac required): You must build the main or dev branch.

### Smartphone requirements
All iPhones which support iOS 15.1 and up.

### Simulators
Start with FreeAPS X on your phone and use the simulated pump and simulated CGM
Or you can read your actual CGM from your Nightscout site and control a simulated pump
Get a feel for the layout of menus and decide if you want to continue
Note – you can leave Loop 3 on the same phone controlling your actual pump and reading the same CGM – the two apps are distinct from each other

### Supported pumps
iAPS uses modified rileylink_ios and OmniBLE libraries to control an insulin pump, thus supporting the same pump list as Loop:

- Omnipod DASH pods (Bluetooth enabled, no RileyLink needed)
- Omnipod “Eros” pods
- Medtronic 515 or 715 (any firmware)
- Medtronic 522 or 722 (any firmware)
- Medtronic 523 or 723 (firmware 2.4 or lower)
- Medtronic Worldwide Veo 554 or 754 (firmware 2.6A or lower)
- Medtronic Canadian/Australian Veo 554 or 754 (firmware 2.7A or lower)

To control an insulin pump, except for DASH, you need to have a RileyLink compatible device: RileyLink, OrangeLink, Pickle, GNARL, EmaLink or similar device.

## Supported CGM
- Direct support using Dexcom app (G5, G6 and G7) on your phone (offline)
- Nightscout BG data source as a CGM (online, e.g., cell or WiFi connection)
- Applications that mimic Nightscout as a CGM (apps like Spike and Diabox) (Offline, e.g., local on your phone)
    - Follow instructions here
- If you build xDrip4iOS with the same bundle identifier as FreeAPS X you get CGM local on your phone
Additional information is found in the Build section
This link shows the list of supported CGM with this code
