# Autotune
:::{admonition} Highlights
:class: important
- Enable autotune unless you have full confidence in your current profile settings. 
- Autotune adjustments are limited by autosens max/min.
:::
---
## What is Autotune?

Autotune is a feature that refines your insulin pump's settings—**basal rates**, **insulin sensitivity factor (ISF)**, and **carb ratio (CR)**—by making small, iterative adjustments based on your last 24 hours of glucose data. Think of it as a long-term fine-tuning tool.

By default, Autotune runs nightly, but you can also run it manually. Each adjustment is minor—up to a 10% change for ISF and CR, and up to a 20% change for basal rates per run. These small changes accumulate over days and weeks, gradually improving the accuracy of your initial profile settings. Autotune's output is limited by the same maximum and minimum ratios as Autosens, ensuring adjustments stay within safe bounds.

---
## How Does Autotune Work?

Autotune doesn't use machine learning or artificial intelligence. Instead, it employs **statistical regression** to compare your recent glucose data with your current profile settings and then suggests adjustments.

Here's a breakdown of how it works for each setting:

* **Basal Rates:** Autotune divides the day into hourly segments. For each hour, it calculates how much your glucose deviated from your target. It then determines the basal rate change needed to correct these deviations. Because insulin has a delayed effect, it applies 20% of this calculated change to the current hour and the two hours prior. If increasing basal, the increase is applied equally to all three hours. If decreasing, the reduction is proportional, meaning the largest basal rates see the biggest decrease.

* **ISF (Insulin Sensitivity Factor):** Autotune identifies the median glucose deviation for the entire day. It then calculates how much your ISF would need to change to eliminate this deviation and applies 10% of that adjustment to your ISF.

* **CR (Carb Ratio):** Autotune analyzes glucose deviations during all mealtimes throughout the day, comparing them to the expected deviations based on your current carb ratio and logged carb intake. It then applies 10% of the calculated adjustment to your CR.

---
## Important Note on Dynamic Settings

Autotune relies on a **profile-based ISF** value to calculate glucose deviations. This is crucial: if you use dynamic functions within iAPS (which adjust your ISF and CR in real-time based on current conditions), Autotune will not use the actual ISF that was active when your loop was running in the past. This can lead to inaccurate basal and ISF adjustments.

Furthermore, Autotune can only operate with a **single daily ISF and CR**. As a result, it may not be suitable for individuals who have varying ISF and CR settings throughout the day. In simple terms, Autotune results can be unreliable if dynamic settings are enabled.

---
## How Does Autotune Differ from Autosens?

* **Autosens** makes rapid, real-time adjustments to your insulin delivery settings with every loop cycle. It's designed to account for immediate biological changes in insulin sensitivity due to factors like time of day, night, or pump site changes. It works on a shorter timescale, typically using data from the last 8 or 24 hours.

* **Autotune**, in contrast, operates on a much longer timescale. It focuses on making slow, consistent adjustments to your baseline profile settings to improve their overall accuracy over weeks. It runs once every 24 hours.

---
## Should You Enable Autotune?

Consider these points before enabling Autotune:

* **If your current profile settings are already well-tuned and accurate,** enabling Autotune might actually worsen your glucose control, especially in scenarios like recovering from illness.
* **If you decide to enable it,** be aware that Autotune's adjustments are limited by your Autosens maximum and minimum ratios. While you can modify these values to give Autotune more flexibility, doing so will also impact Autosens, dynamic ISF, dynamic CR, and basal adjustments.

Instead of continuously relying on Autotune for daily adjustments, a better approach is to **periodically review your settings** after a few weeks of Autotune running. Note the new values it suggests and then manually update your main profile settings to match them. This gives Autotune a fresh starting point for any future fine-tuning.

