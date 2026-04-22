# Overview

## What is iAPS?

Powered by the OpenAPS algorithm, **iAPS is an open-source Artificial Pancreas System** designed to simplify diabetes management. By leveraging your specific settings, carbohydrate information, and historical data, it aims to **automate insulin delivery** and significantly **cut down on the daily effort** you put into managing your diabetes.

We encourage you to explore all your options before committing to iAPS. Consider commercial alternatives like the **Tandem IQ** and **Omnipod 5**, or other well-known open-source solutions such as **Loop** and **AndroidAPS**.

Important: iAPS is not approved by any healthcare authority. **You are responsible for building and operating this system at your own risk**.

## Getting Started

Before you begin with iAPS, it's helpful to have a basic grasp of concepts like **ICR (Insulin-to-Carbohydrate Ratio)**, **ISF (Insulin Sensitivity Factor)**, and **basal rates**. If you're unsure about these or need help figuring out your personal settings, please refer to the relevant documentation.

To use iAPS, you'll need to **build the application from its source code**. Don't worry, this doesn't require advanced technical skills, but it is a time-consuming process. You might find yourself needing several sessions to complete your first build.

Once installed, you'll configure your settings. By default, iAPS will act much like your current pump, though it might suggest temporary basal adjustments occasionally. The real power of iAPS unlocks when you enable **"Closed Loop"**, enabling **automatic bolus features**, and **autotune**. As you get more confident with the app and your settings, these are generally the first three features you'll want to configure:

* **Enable Closed Loop for automation**.
* **Increase Max IOB (Insulin on Board)** by setting it to "average meal bolus + 3x max daily basal."
* **Enable SMB (Super Micro Bolus) and UAM (Unannounced Meals)** for automatic bolusing (but make sure your ISF is optimized before turning these on).

For more detailed information on configuring iAPS, please see the "Configure" section.
