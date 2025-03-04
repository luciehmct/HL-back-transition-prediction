# Feature Selection

Most of the features were retained, even though their predictive power was not always certain. This decision was based on the hypothesis that, while certain features did not show clear patterns for prediction, the dynamics of plasma are highly complex. Therefore, potentially important features that could contribute to the model’s ability to capture the intricate behavior of plasma transitions were not excluded.

The features are:

---

## Wtot
Selected due to its direct relevance to the plasma energy.

<img src="plots/Wtot_boxplot.png" width="800px"/>  
<img src="plots/Wtot_distribution.png" width="800px"/>

---

## DML
Fully compensated plasma toroidal flux measured with the diamagnetic loop (Units = Wb).  
Steep drops in DML values are observed at HL transition times. These drops show a good correlation with Wtot, but are not exclusively indicative of HL transitions.

<img src="plots/DMLplot.png" width="800px"/>  
<img src="plots/DML_boxplot.png" width="800px"/>  
<img src="plots/DML_distribution.png" width="800px"/>

---

## FIR_LIDs_core
Far InfraRed (FIR) Line Integrated Density (LID) in the core plasma region, essential for understanding the average plasma density along a specific line of sight. Steep drops in FIR_LIDs_core values are observed at HL transition times, which correspond well with Wtot drops. However, these drops are not necessarily restricted to HL transitions.

<img src="plots/FIR_LIDs_core_plot.png" width="800px"/>  
<img src="plots/FIR_LIDs_core_boxplot.png" width="800px"/>  
<img src="plots/FIR_LIDs_core_distribution.png" width="800px"/>

---

## FIR_LIDs_LFS
Far InfraRed (FIR) Line Integrated Density (LID) in the Low Field Side (LFS) of the tokamak, where the magnetic field is weaker. Steep drops in FIR_LIDs_LFS values at HL transition times correlate with Wtot, but these drops are not exclusively due to HL transitions.

<img src="plots/FIR_LIDs_LFS_plot.png" width="800px"/>  
<img src="plots/FIR_LIDs_LFS_boxplot.png" width="800px"/>  
<img src="plots/FIR_LIDs_LFS_distribution.png" width="800px"/>

---

## FIR_LIDs_HFS
Far InfraRed (FIR) Line Integrated Density (LID) in the High Field Side (HFS) of the tokamak, where the magnetic field is stronger. Steep drops in FIR_LIDs_HFS values are observed at HL transition times, showing a good correlation with Wtot, though not uniquely indicating HL transitions.

<img src="plots/FIR_LIDs_HFS_plot.png" width="800px"/>  
<img src="plots/FIR_LIDs_HFS_boxplot.png" width="800px"/>  
<img src="plots/FIR_LIDs_HFS_distribution.png" width="800px"/>

---

## IPLA
Plasma current amplitude, measured in amperes (A). This feature did not show any distinct patterns or useful information in the first exploration, but may nonetheless be useful for prediction.

<img src="plots/IPLA_plot.png" width="800px"/>  
<img src="plots/IPLA_boxplot.png" width="800px"/>  
<img src="plots/IPLA_distribution.png" width="800px"/>

---

## IP
Total plasma current, measured in amperes (A). Although potentially informative, this feature did not display clear patterns in the initial analysis. The distribution showed a consistent single peak for transitions, whereas non-transition windows exhibited either a single peak or a more varied distribution.

<img src="plots/IP_plot.png" width="800px"/>  
<img src="plots/IP_boxplot.png" width="800px"/>  
<img src="plots/IP_distribution.png" width="800px"/>  
<img src="plots/IP2_distribution.png" width="800px"/>

---

## Halpha13
Hydrogen's Balmer-alpha spectral line related to radiation from the plasma. Spikes in Halpha13 are observed during HL transitions, typically preceded by high-frequency oscillations of moderate amplitude. Thus, the FFT of Halpha13 was used for further analysis.

<img src="plots/Halpha13_plot.png" width="800px"/>  
<img src="plots/Halpha13_boxplot.png" width="800px"/>  
<img src="plots/Halpha13_distribution.png" width="800px"/>  
<img src="plots/FFT_Halpha13_plot.png" width="800px"/>  
<img src="plots/FFT_comp_Halpha13_plot.png" width="800px"/>

---

## PECRH
The initial plot of this feature did not reveal any useful patterns that could help the predictions.

<img src="plots/PECRH_plot.png" width="800px"/>  
<img src="plots/PECRH_boxplot.png" width="800px"/>  
<img src="plots/PECRH_distribution.png" width="800px"/>

---

## Z_axis
Small drops are observed at HL times, but these are not restricted to HL events, and the utility of this feature remains uncertain.

<img src="plots/Z_axis_plot.png" width="800px"/>  
<img src="plots/Z_axis_boxplot.png" width="800px"/>  
<img src="plots/Z_axis_distribution.png" width="800px"/>

---

## POHM
This feature did not reveal significant patterns during the initial analysis and was thus considered less useful.

<img src="plots/POHM_plot.png" width="800px"/>  
<img src="plots/POHM_boxplot.png" width="800px"/>  
<img src="plots/POHM_distribution.png" width="800px"/>

---

## Ne_rho_z35
From PC1 during HL transition times. Changes in the slope are observed close to HL transition periods.

<img src="plots/Ne_rho_z35_plot.png" width="800px"/>  
<img src="plots/Ne_rho_z35_boxplot.png" width="800px"/>  
<img src="plots/Ne_rho_z35_distribution.png" width="800px"/>

---

## Te_rho_z1 and Te_rho_z2
From PC2 during HL transition times. Changes in the slope are consistently observed around HL transition points.

<img src="plots/Te_rho_z1_plot.png" width="800px"/>  
<img src="plots/Te_rho_z1_boxplot.png" width="800px"/>  
<img src="plots/Te_rho_z2_plot.png" width="800px"/>  
<img src="plots/Te_rho_z2_boxplot.png" width="800px"/>
