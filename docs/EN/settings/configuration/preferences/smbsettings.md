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
Enabling this setting allows SMBs to be delivered if your blood sugar is predicted to go above target. 

SMBs will remain on if you have a low temporary target set, but will be fully disabled if a high temporary target is set (unless "[Allow SMB With High Temptarget](#allow-smb-with-high-temptarget)" is enabled).

There are limitations on the size of SMBs. [See the OpenAPS documentation for more information.](https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/oref1.html#understanding-super-micro-bolus-smb)

## Max Delta-BG Threshold SMB
This is a safety limiter that looks at the difference between your last two blood glucose readings. If the difference is large, iAPS suspects them to be incorrect and will suspend SMB delivery accordingly.

You can adjust how much of a difference should be allowed before SMBs are delivered. 30% is advised for closed loop.

## Enable SMB With COB
SMBs will be enabled if you currently have carbs on board (COB) to help you deal with meal spikes. This feature should be enabled if you want to use UAM.

If you already have "[Enable SMB Always](#enable-smb-always)" on, this feature is redundent and does not need to be configured.

## Enable SMB with Temptarget
SMBs will be enabled if you have set a lower blood sugar target temporarily. This will allow you to reach your target faster.

If you already have "[Enable SMB Always](#enable-smb-always)" on, this feature is redundent and does not need to be configured.

## Enable SMB After Carbs
SMBs will be enabled if you had carbs within the last 6 hours to help with meal spikes.

If you already have "[Enable SMB Always](#enable-smb-always)" on, this feature is redundent and does not need to be configured.

## Allow SMB With High Temptarget
By default, iAPS will not allow SMBs if you have a temporary blood glucose target set above 5.5 mmol/L (100 mg/dL), even if "[Enable SMB Always](#enable-smb-always)" is toggled on. Toggling this feature on will disable that safety check and not prevent SMBs when a high temporary target is set, as long as SMBs are otherise enabled.

## Enable SMB With High BG
This allows SMBs to occur above a certain blood glucose level. Some individuals with variable sensitivity may find that SMBs can cause low blood sugars and rollercoasters when near their target. 

If you are in closed loop and rely heavily on UAM (i.e. you do not bolus for your meals) you should keep this feature disabled so iAPS can provide you with the necessary insulin if you are predicted to go high. Else if you are currently within your target blood glucose range, SMBs will not be delivered.

If you already have "[Enable SMB Always](#enable-smb-always)" on, this feature is redundent and does not need to be configured.

## ... When Blood Glucose is Over (mg/dl)
See the above setting for more information. This allows you to configure the target at which SMBs will be enabled.

## Enable UAM
With this option enabled, the SMB algorithm can recognize unannounced meals. This is helpful if you forget to tell iAPS about your carbs or estimate your carbs wrong and the amount of entered carbs is wrong or if a meal with lots of fat and protein has a longer duration than expected. Without any carb entry, UAM can recognize fast glucose increasements caused by carbs, illnesss, or counterregulatory hormones, and tries to adjust it with SMBs. This also works the opposite way: if there is a fast glucose decreasement, it can stop SMBs earlier.

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
