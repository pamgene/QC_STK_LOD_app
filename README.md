# QC_STK_LOD_app

The `STK_QC_LOD_app` works based on Limit of Detection (LOD) of STK S100 signal to exclude low-signal peptides.

The LOD is calculated as the S100 of the prephosphorylated peptides * 0.0026.
Peptides with S100 signal above LOD are considered as present peptides, while peptides below are considered as not present.

Next, the app calculates the ratio of samples above the LOD, per peptide. This is equivalent to the "fractionPresent" factor in the [PTK_QC](https://github.com/pamgene/QC_PTK_app). Based on this, a threshold can be set, to include only peptides with values >= this threshold, in the next step (log/VSN step). 
The default threshold is 0.25, which allows to keep only those peptides which are present in more than one condition, based on a 4-condition experiment. Therefore, it is recommended to always revise this threshold based on the experiment! 

#### Output relations:
- qc_stk_thr.ratio: the ratio of samples above the LOD, per peptide. Equivalent to the "fractionPresent" factor in the PTK QC.


#### Details of LOD calculation

Based on 11 datasets of technical replicates, the S100 signal at 30% CV (CV within an instrument unit) was measured.
The signal strength is correlated with the signal strength of the prephosphorylated peptides. 
Thus, there is a consistent ratio of the S100 signal at 30% CV / S100 signal of the prephoshorylated peptides: this is 0.0026.

0.0026 = (S100 signal at 30% CV of technical replicates) / (S100 of prephoshorylated peptides)

Thus:

LOD = 0.0026 * S100 of prephoshorylated peptides






