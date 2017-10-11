# File & Repo Structure

This is an outline of the structure of the repoisitory on GitHub. See docs\process-for-running-code.md for information on setup. 

- archive *Old files*
- - analysis.R *An earlier version of the code, taking into account landuse*
- docs *Supporting documentation*
- - townsend-defination
- - faq.md *Frequently Asked Questions*
- - file-information.md *This file*
- - process-for-running-code.md *File outlining the setup process and how to run the code to create the grids*
- input *Folder for input census data and supporting documents, see process-for-running-code.md for setup*
- output *Folder containing generated grids*
- - folder-placeholder.txt *Empty file to ensure output folder exists in repoisitory*
- R-functions *Functions supporting R script*
- - funAdjustPop.R
- - funAllocateContiguousRegions.R
- - funAllocateToGrid.R
- - funAreaWeightedSumLanduse.R
- - funAreaWeightedSumOverlayGrid.R
- - funCalcRate.R
- - funDataSummary.R
- - funDataSummaryNoOverlay.R
- - funExportGrid.R
- - funGridSmoothing.R
- - funGridSmoothingIterative.R
- - funPreProcessing.R
- tmp *Folder for tempoary files*
- townsend *Files for townsend variable generation*
- - summary_stats.csv
- - summary_stats.csvt
- - summary_stats.R
- - townsend-score-calculation-1971.R
- - townsend-score-calculation-1981.R
- - townsend-score-calculation-1991.R
- - townsend-score-calculation-2001.R
- - townsend-score-calculation-2011.R
