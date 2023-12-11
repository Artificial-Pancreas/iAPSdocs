# Add Customizations to iAPS

Here are a few ways to customize iAPS' code to better suit your needs. Please be very careful when editing any code.

## Bypass Authentification for Bolusing

Depending on your iPhone Settings and model, you may have Face ID or Touch ID enabled. Those security features will also be used to authenticate bolus delivery in iAPS. You can choose to disable authentication (i.e., not require Face ID, Touch ID, or passcode for bolusing) through the following code customization.

:::{admonition} Caution
:class: caution
- If you disable this, you are removing an important safety feature.
- In addition to authenticating every manual bolus, this helps to protect against sleep bolusing and pocket bolusing.
:::

Edit line 28 of the file `FreeAPS/Sources/Services/UnlockManager/UnlockManager.swift`.

Code before modification: `if context.canEvaluatePolicy(.deviceOwnerAuthentication, error: &error) {`

Code after modification: `if false && context.canEvaluatePolicy(.deviceOwnerAuthentication, error: &error) {`

## Omnipod: Add Extra Insulin on Insertion

The default value is 0.0 U of extra insulin. If you use this customization, start with a small number and work your way up. If you are coming from manual podding and routinely gave yourself an extra bolus with your PDM at pod change time, you may not need nearly as much with iAPS - be conservative.

Note that iAPS does not include the amount of insulin in the prime or insertion steps in your IOB. The pod reports every pulse that it delivers to iAPS. If you look in the Pod Settings insulin delivered row, that is the total delivered by the pod minus the (prime plus insertion) amounts. The only way to know that you successfully made this change is to count the clicks. Normal insertion is 0.5 U (0.5 U / 0.05 U per click = 10 clicks). So if you add 0.25 U to the "extra" value, you should get 0.25 / 0.05 = 5 extra clicks. In other words, 15 total clicks after you press insert.

This code change is found in one location for Eros Pods an another for DASH Pods. I tend to change both files just in case, but if you're only using one kind of pod, that is not really necessary.

For DASH, edit line 82 of the file `Dependencies/OmniBLE/OmniBLE/OmnipodCommon/Pod.swift`.

Code before modification: `public static let cannulaInsertionUnitsExtra = 0.0`

Code after modification adding 0.25U of insulin: `public static let cannulaInsertionUnitsExtra = 0.25`

For Eros, edit line 84 of the file `Dependencies/OmniKit/OmniKit/OmnipodCommon/Pod.swift`.

Code before modification: `public static let cannulaInsertionUnitsExtra = 0.0`

Code after modification adding 0.25U of insulin: `public static let cannulaInsertionUnitsExtra = 0.25`
