---
title: Magtonometer Calibration
weight: 6
---

LGDXRobot2 supports ICM-20948, the Magtonometer required manulally calibrating. The **Magtonometer Calibration** supports both **Hard Iron** and **Soft Iron** calibration methods.

Switch to the **Magtonometer Calibration** tab to view the calibration parameters. If they are not visible, press **Refresh**.

## Current Configuration

The current configuration shows the calibration parameters for the magnetometer. These parameters are used to calculate the magnetometer output.

Press **Refresh** to update the current configuration.

Press **Reset Calibration Data** to reset the parameters to their uncalibrated state.

![Screenshot of the Current Configuration](../img/mag_current_conf.png)

## Custom Configuration

The custom configuration allows the calibration parameters to be entered manually. Then press **Send** to save the parameters.

To discard the soft iron calibration, enter an identity matrix with **1** on the diagonal and **0** on the off-diagonal elements.

![Screenshot of the Custom Configuration](../img/mag_custom_conf.png)

## Magtonometer Calibration

Magnetometer calibration obtains parameters for **Hard Iron** and **Soft Iron**.

![Screenshot of the Magnetometer Calibration](../img/mag_calibration.png)

### Calibration

1. The controller board sends calibrated data, so ensure the **Current Configuration** shows the default values. If not, press **Reset Calibration Data** to reset the parameters to their uncalibrated state.
2. Press **Start Calibration** to begin the calibration.
3. Rotate the controller board to collect data.
4. Observe that the calibration data is being updated.
5. Press **Stop Calibration** to end the calibration.
6. Press **Send** to save the parameters, or press **Send Hard Iron** to save the parameters specifically for Hard Iron.

The Soft Iron calibration is under development.  
{.alert .alert-info}

### Test Calibration

1. Ensure that **Current Configuration** shows the correct values. If not, press **Refresh** to update the configuration.
2. Press **Start Testing** to begin the test.
3. Rotate the controller board to collect data.
4. Observe the calibration chart.
5. Press **Stop Testing** to end the test.
