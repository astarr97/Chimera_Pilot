# Chimera_Pilot

This describes the code associated with our preprint: https://doi.org/10.1101/2024.05.06.592777.  This code is not actively maintained.  The general workflow is that the scripts in CellRanger_Scripts were used to perform the alignment and then Demultiplex_cluster_final.ipynb and Final_postclustering.ipynb were used to do all of the clustering through computing the intrinsic, extrinsic, and intrinsic-extrinsic interaction divergence.  After that, most other scripts are connected to different figures or subfigures in the first biorxiv version that was uploaded and there is generally no strong ordering.  There are also several motifs that are repeated quite often and generally fall into a few different categories for the remaining notebooks: enrichment analysis with GSEAPY, plotting gene expression levels, or image analysis.  

Please see the preprint for methods details.  Alignment and quantification was performed using CellRanger and the scripts in "CellRanger_Scripts".

After alignment, the code in Demultiplex_cluster_final.ipynb was used to determine the sex and species of each cell in each sample and do all clustering and subclustering. The general workflow is very similar to the standard scanpy workflow. A cell was assigned to mouse if greater than or equal to 70% of aligned reads aligned to the mouse genome, assigned to rat if greater than or equal to 70% of aligned reads aligned to the rat genome, and discarded as a doublet otherwise. We first grossly clustered the cells into neural, connective, and blood and then subclustered the two tissues (neural and connective) that were used for the remainder of the analysis. 

Final_postclustering.ipynb contains the code used to decompose gene expression divergence into its extrinsic, intrinisic, and interaction components. It also includes the code to compute the normalized counts.

Regression_Preparation_SuppFig4-10_AnalysisP... was used to compute the variables that went into the spearman correlation in Figure S12 and do the enrichment analysis/figure-making for everything related to the supplemental text.  This includes using the data from Cardoso-Moreira et al. to whether differences in developmental timing of gene expression might affect our results.  The actual figures for S12 (as well as 2G) were made in Fig_S12_Fig_2G.ipynb

Fig_2A-F.ipynb was used to make those subfigures (this is figure 3 in the updated version).  It also contains the code to compute the total divergence explained from intrinsic, extrinsic, and interaction components across all genes for each cell type.

Enrichment_Figures3-4_SFigs.ipynb was used to do the ontology enrichment analysis for signed extrinsic/intrinsic/interaction divergence and make associated figures.
Fig3_TF_Enrichment.ipynb was used to do the TF-target enrichment analysis, work on Xbp1, and make associated figures.  The code is highly similar to Enrichment_Figures3-4_SFigs.ipynb.

Image_Analysis_Final.ipynb was used to do the immunofluorescence quantification and Fig5D-E_Image_Figures.ipynb was used to make the associated barplots (the actual IF images were made in ImageJ). See the paper for more details in how the images were processed.

Imprinting_Analysis.ipynb and Imprinting_Figures.ipynb were used to do the analysis/figure making for imprinting-related things using our data.  This includes doing the enrichment analysis for imprinted genes in our data and other rat-mouse chimera datasets.  ExVivo_HumMac.ipynb as used to do the analysis and figure making related to the ex-vivo data from human-monkey chimeric embryos. Heart_Imprinting.ipynb was used to do the analysis and figure making related to embryonic hearts from chimeras. Parathyroid_Fig6H.ipynb was used to do the analysis and figure making related to the adult parathyroid data from chimeras.

Neuron_Progenitor_Final_Fig5G.ipynb was used to do the analysis on the temporal order of neurogenesis.

Making_Tables.ipynb was used to collate supplemental tables 1-3.
Swarmplots_Various_SuppFigs.ipynb was used to make all the swarmplots of gene expression per-cell that correspond to barplots.
UMAP_FigS1-S2.ipynb was used to make the UMAP plots, it was not used for any clustering.
