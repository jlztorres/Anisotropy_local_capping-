# Anisotropy_local_capping-
local smoothing for outliers - Antamina ore deposit


To speed up the outlier definition process and allow the use of weighted data to be used in the definition of local outliers, modifications to the outlier detection program were made.  Specifically:
•	Up to 6 different risk levels can be used in the same program run.  As an example, for copper, 12.5%, 15%, 17.5%, 20%, 22.5%, and 25% can be considered all in the same program run (no need to run the program 6 times).  The program will output an indicator (composite capped or not) and a suggested capped value for each threshold.  To minimize the output, other variables such as search pass, variance, average with, average without, etc. are no longer output.
•	The data are sorted prior to selecting the nearby data and data that are distant are excluded (per composite).  This simple “super block” type optimization reduces the number of data considered for each sample.
•	The local mean can now be computed with distance based weights.  The weighting function is 1/(search expansion +1), so any samples located in the first volume considered (including the composite being considered as an outlier) receive a weight of 1.  If a sample is found in the first search expansion it receives a weight of 1/2 (second expansion 1/3, etc).  The final average grades (with and without the center composite) are then weighted averages.
The current version requires a little under an hour (on my machine) to process all composites in the 2015 database at 6 risk thresholds.  
