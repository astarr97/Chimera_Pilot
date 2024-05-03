# Chimera_Pilot

This describes the code associated with a soon-to-be-released biorxiv preprint (will add link here).  This code is not actively maintained.

Please see the preprint for methods details.  Alignment and quantification was performed using CellRanger and the scripts in "CellRanger_Scripts".

After alignment, the code in Demultiplex_cluster_final.ipynb was used to determine the sex and species of each sample and do all clustering and subclustering.
Final_postclustering.ipynb was used to pseudobulk and compute extrinsic, intrinisic, and interaction components.
Regression_Preparation_SuppFig4-10_AnalysisP... was used to compute the variables that went into the spearman correlation in Figure S12 and do the enrichment analysis/figure-making for everything related to the supplemental text.  The actual figures for S12 (as well as 2G) were made in Fig_S12_Fig_2G.ipynb
Fig_2A-F.ipynb was used to make those figures.
Enrichment_Figures3-4_SFigs.ipynb was used to do the ontology enrichment analysis and make associated figures.
Fig3_TF_Enrichment.ipynb was used to do the TF-target enrichment analysis, work on Xbp1, and make associated figures.
Image_Analysis_Final.ipynb was used to do the immunofluorescence quantification and Fig5D-E_Image_Figures.ipynb was used to make the associated barplots (the actual IF images were done in ImageJ).
Imprinting_Analysis.ipynb and Imprinting_Figures.ipynb were used to do the analysis/figure making for imprinting-related things using our data.
Neuron_Progenitor_Final_Fig5G.ipynb was used to do the analysis on the temporal order of neurogenesis.
Heart_Imprinting.ipynb was used to do the analysis and figure making related to embryonic hearts from chimeras.
Parathyroid_Fig6H.ipynb was used to do the analysis and figure making related to the adult parathyroid data from chimeras.
ExVivo_HumMac.ipynb as used to do the analysis and figure making related to the ex-vivo data from human-monkey chimeric embryos.
Making_Tables.ipynb was used to collate supplemental tables 1-3.
Swarmplots_Various_SuppFigs.ipynb was used to make all the swarmplots of gene expression per-cell that correspond to barplots.
UMAP_FigS1-S2.ipynb was used to make the UMAP plots, it was not used for any clustering.
