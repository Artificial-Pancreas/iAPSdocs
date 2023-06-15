# PLEASE NOTE THIS DOCUMENTATION IS A DRAFT ONLY AND SHOULD YET NOT BE FOLLOWED FOR SETTING UP AND OPERATING IAPS!!

# What is iAPS?
iAPS is a open source artifical pancrease system based on the OpenAPS algorithm. Using your inputted settings, carbohydrates and historical data, it aims to automate insulin delivery to reduce the time spend managing your diabetes. Before starting with iAPS, you should consider alternative commercial options such as the Tandem IQ and Omnipod 5, or other open source applications like Loop and AndroidAPS. iAPS is not approved by any health care authority. You are building and running this system at your own risk.

# Getting Started
Before starting with iAPS, you should have a basic understanding of what ICR, ISF and basal rates are. If you do not have a clear understanding, or require some help identifying your settings, please read the appropriate documentation.

To use iAPS, you are required to build the application from the source code. This does not require substantial technical know-how but is a time consuming process. You may need to carry this out through several sessions on your first attempt.

Upon installation, you will need to configure your settings appropriately. By default iAPS acts no different than that of your pump, with the exception that it may recommend temporary basals from time to time. The magic happens by turning on "Closed Loop", enabling automatic bolus features, and turning on autotune. In general, these are the first three settings you will want to configure as you gain confidence in the app and your settings:

- Enable Closed Loop for automation
- Increase Max IOB via "average mealbolus + 3x max daily basal"
- Enable SMB and UAM for automatic bolusing (ensure your ISF is optimized before enabling this)
See Configure for more information on iAPS configuration.

# Contribution
iAPS is built by a volunteer community. If you are interested in helping as a programmer, you can help contribute to iAPS, or OpenAPS code base.

You can also provide support in online support groups by helping them adjust their settings and troubleshoot common errors.

(index-Overview)=

```{toctree}
:caption: Overview
:maxdepth: 2

./Getting-Started/Overview.md
./Getting-Started/iphone.md
./Getting-Started/pump.md

```

(index-Configuration)=

```{toctree}
:caption: Configuration

./Configuration/Configure.md
./Configuration/Devices.md
./Configuration/transition-qa.md

```
(index-Settings-Basics)=

```{toctree}
:caption: Settings Basics

./settings/configuration/autotune.md
./settings/configuration/basalprofile.md
./settings/configuration/carbratios.md
./settings/configuration/insulinsensitivites.md
./settings/configuration/pumpsettings.md
./settings/configuration/targetranges.md
./settings/devices/cgm.md
./settings/devices/pump.md
./settings/services/applehealth.md
./settings/services/fatprotein.md
./settings/services/nightscout.md
./settings/services/notifications.md

```

(index-Settings-Advanced)=

```{toctree}
:caption: Settings Advanced

./settings/configuration/concepts/autosens-dynamic.md
./settings/configuration/concepts/sigmoid.md
./settings/configuration/concepts/asmb-uam.md
./settings/configuration/preferences/dynamicsettings.md
./settings/configuration/preferences/freeapsx.md
./settings/configuration/preferences/mainsettings.md
./settings/configuration/preferences/othersettings.md
./settings/configuration/preferences/smbsettings.md
./settings/configuration/preferences/targetsettings.md

```

(index-Operate)=

```{toctree}
:caption: Operate

Build <./operate/build.md>

Interface <./operate/interface.md>

Temp Target <./operate/temptarget.md>

Troubleshoot <./operate/troubleshoot.md>

```


(index-resources)=

```{toctree}
:caption: Resources

Interface <./resources/alternative.md>

Citations <./operate/citations.md>

```
