# OpenAPS SMB Settings
:::{admonition} Highlights
:class: important
- Enable SMB Always: Most commonly enabled setting; allows iAPS to provide small correction boluses to make rapid blood sugar adjustments. If you want to configure SMB to only run in certain conditions read below.
- Max Delta-BG Threshold SMB: Change to 0.3 (30%) for closed loop with UAM enabled.
- Enable UAM: Enable to allow iAPS to bolus for detected meals. Pre-meal bolusing is still advised even with this feature enabled.
- Max SMB Basal Minutes: Increase to allow SMB to give more insulin in one bolus. Increase if struggling with fasting highs.
- Max UAM SMB Basal Minutes: Increase to allow UAM to give more insulin in one bolus. Increase if struggling with meal or hormonal highs.
- Bolus Increment: Change to 0.05 for Omnipod users
:::
## Enable SMB Always
Enabling this setting allows SMBs to be delivered if blood sugar is above, or predicted to rise above, your target blood glucose (BG) set in the "Target Glucose" setting or when using a temporary target.

Some users set a low temporary target, for example, before meals. In this case, with "Enable SMB Always" selected, SMBs will be delivered to assist in bringing your blood sugar to this lower target. 

In other instances, such as when exercising, users may set a high temporary target to avoid low BG. In this case, SMBs are disabled. Note: SMBs will be delivered, even with a high temporary target, if you also select "[Allow SMB With High Temptarget](#allow-smb-with-high-temptarget)" (see below). 

## Max Delta-BG Threshold SMB
This is a safety feature that disables SMBs temporarily, if iAPS suspects your BG reading is wrong, based on a large difference between the last two readings. 

Note: The recommended setting is  0.3 (30%) in closed loop to allow iAPS to use SMB when BG is rising quickly. 

## Enable SMB With COB
If you have carbs on board (COB), SMBs will be enabled to reduce meal spikes. 

## Enable SMB with Temptarget
SMBs will be enabled if you have set a low temporary target, for example, to reduce BG before meals. Enabling this setting, when using a low temporary target, will allow you to reach your target faster.

## Enable SMB After Carbs
SMBs will be enabled, if you have entered carbs within the last 6 hours — even with 0 COB — to help with meal spikes. 
This setting is useful when COB shows 0, but your BG is still rising from undercounted carbs, fat or protein. It can also help when your settings are off.

## Allow SMB With High Temptarget
Some users temporarily set a higher than normal BG target to avoid insulin delivery, for example, after a low blood sugar. 
By default, iAPS disables SMBs if you have a temporary BG target set above 100 mg/dL (5.5 mmol), even when "[Enable SMB Always](#enable-smb-always)" is selected. This setting will remove that safety check. 

Note: Most users disable this setting unless they have a specific need for it, because it overrides a default iAPS safety check.

## Enable SMB With High BG
For a number of reasons, some users may find that SMBs cause low blood sugars and rollercoastering when near their target. If this is a concern, you can enter a BG target in the setting below to keep SMBs from being delivered below that level.

## ... When Blood Glucose is Over (mg/dl)
See the above setting for more information. This setting allows you to set the BG target at which SMBs will be enabled.

## Enable UAM
Enable Unannounced Meal (UAM) detection to allow iAPS to bolus and deliver temp basals in response to rising BG because of underestimated carbs or when no carbs were announced. UAM can also help if a meal with lots of fat and protein has a longer duration than expected. 

The Enable UAM feature can also act to reduce lows. With this selection enabled, when iAPS detects that BG is quickly dropping, it can stop SMB and basal doses.  

Note: Pre-meal bolusing is still advised even with this feature enabled.

## Max SMB Basal Minutes
Max SMB Basal minutes is one of the major limiters of the size of SMBs. For more information on what limits SMB size, please view<a href = "https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/oref1.html#understanding-super-micro-bolus-smb"> the OpenAPS documentation.</a> SMBs are limited by the amount of scheduled basal insulin in your profile settings.

Example: Bill has a basal profile setting of 1.5 U/hr. He has a "Max SMB Basal minutes" setting of 30 min:

- 1.5 U / 60 min * 30 min = 0.75 U

Each of Bill's SMBs are thus limited to a maximum of 0.75 U by Max SMB Basal Minutes. 

If you find that iAPS is giving insignificant boluses every 5 minutes, it may be being limited by your [Max IOB](./mainsettings.md#max-iob) or [Max SMB basal minutes](#max-smb-basal-minutes). First, confirm your basal rates are adequate. Then you can experiment with increasing this number so iAPS is able to provide larger SMBs for more rapid blood sugar control.

## Max UAM SMB Basal Minutes
See "[Max SMB Basal Minutes](#max-smb-basal-minutes)" above and<a href = "https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/oref1.html#understanding-super-micro-bolus-smb"> the OpenAPS documentation</a> for more information on the limiters of SMBs. 

This limits the size of SMBs UAM can deliver when it detects a meal, by the amount of scheduled basal insulin in your profile settings. You can configure this setting to make UAM more or less aggressive against meal spikes. Note that SMBs are also limited by your [Max IOB](./mainsettings.md#max-iob) and [SMB DeliveryRatio](#smb-deliveryratio).

## SMB DeliveryRatio
This is a safety limiter. iAPS determines how much insulin is required to get you back within target range. If SMB is enabled, iAPS then delivers an SMB, that defaults to half the required insulin.

This setting allows you to boost or reduce what fraction of the required insulin is delivered in a single SMB. It is recommended you look at your basal profile, [Max SMB basal minutes](#max-smb-basal-minutes), [Max UAM SMB Basal Minutes](#max-uam-smb-basal-minutes), and [Max IOB](./mainsettings.md#max-iob) before you adjust this setting.

## SMB Interval
The minimum interval between SMB boluses. SMBs will be delivered at this rate or less as needed.

## Bolus Increment
The minimum amount of insulin that can be bolused by iAPS via an SMB. This is determined by your pump hardware.
