# Chimera_Pilot

This describes the code associated with our preprint: https://doi.org/10.1101/2024.05.06.592777.  This code is not actively maintained.  It is worth noting that there are also several motifs that are repeated quite often and generally fall into a few different categories for the remaining notebooks: enrichment analysis with GSEAPY, plotting gene expression levels, or image analysis. For example, the code to plot gene expression levels is copied into several notebooks where it might be slightly altered depending on what was needed for that figure. The general workflow and dependencies is as follows:

First, we used the scripts in CellRanger_Scripts were used to perform the alignment on a computer cluster and download the matrices output by CellRanger.  Both the raw fastq files and resulting anndata objects (described below) are available here: [https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE266218).

Then, Demultiplex_cluster_final.ipynb was used to determine the species of origin for each cell, do basic normalization and preprocessing, cluster, and then subcluster the data to identify cell types. A cell was assigned to mouse if greater than or equal to 70% of aligned reads aligned to the mouse genome, assigned to rat if greater than or equal to 70% of aligned reads aligned to the rat genome, and discarded as a doublet otherwise. We first grossly clustered the cells into neural, connective, and blood and then subclustered the two tissues (neural and connective) that were used for the remainder of the analysis. This resulted in 5 anndata objects (again available on GEO).  GSE266218_All_Cells_Start.h5ad contains the raw counts and is used throughout whereas the other four anndata contain the cluster/subcluster information for the cell types/tissues included in the names of the file.  

Next, Final_postclustering.ipynb was used to filter out lowly expressed genes, normalize counts using the procedure described in the main text, and then decompose expression divergence into intrinsic, extrinsic, and intrinsic-extrinsic interaction. This creates the main inputs to most of the rest of the scripts including cell type counts.  With this output, some minor scripts can be used.  For example, UMAP_FigS1-S2.ipynb can be used to create the UMAP plots in the supplement.  The swarmplots of per cell normalized counts can be made with Swarmplots_Various_SuppFigs.ipynb. You can also do the analysis on neuronal progenitors and neurons using Neuron_Progenitor_Final_Fig5G.ipynb.

Next, it makes sense to download the data from Cardoso-Moreira et al. (also referred to as Kaessmann throughout the code), we downloaded the rat and mouse rpkm from this link: http://evodevoapp.kaessmannlab.org. With this downloaded, you can run Regression_Preparation_SuppFig4-10_AnalysisPlotting.ipynb to create input files needed for some other scripts and recreate the analysis from Supplemental Text 1 on developmentally dynamic gene expression.
 
After running this, you can use Fig3_TF_Enrichment.ipynb to recreate the results on Xbp1 and figure 3 in the previous version (now figure 4 in the updated version).  This includes testing for enrichment of TF targets in intrinsic/extrinsic genes.  You can use Fig_2A-F.ipynb to plot expression levels per gene in different conditions and recreate the plots from the previous figure 2 (now figure 3 in the updated version).  Fig_2A-F.ipynb also contains the code to compute the total divergence explained from intrinsic, extrinsic, and interaction components across all genes for each cell type.  You can use Imprinting_Analysis.ipynb in conjunction with the list of mouse imprinted genes at https://www.geneimprint.com/site/home through the “gene by species” tab to recreate the analysis of imprinted genes and Imprinting_Figures.ipynb to make associated figures.  You can use Fig_S12_Fig_2G.ipynb to recreate 2G (now 3G) and Fig S12. This relies on Regression_Preparation_SuppFig4-10_AnalysisPlotting.ipynb which was used to compute the variables that went into the spearman correlation in Figure S12.

For the analysis of the immunostaining related to figure 5 (now figure 6), Image_Analysis_Final.ipynb was used to do the immunofluorescence quantification and Fig5D-E_Image_Figures.ipynb was used to make the associated barplots (the actual IF images were made in ImageJ). See the paper for more details in how the images were processed.  You will need the results from Final_postclustering.ipynb to make the plots.

ExVivo_HumMac.ipynb as used to do the analysis and figure making related to the ex-vivo data from human-monkey chimeric embryos. The transcripts per million (TPM) matrices for human-macaque chimeric embryos and wildtype human embryos from GEO: https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE155381 and https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE109555 respectively.

Heart_Imprinting.ipynb was used to do the analysis and figure making related to embryonic hearts from chimeras. The counts matrices and associated metadata (including the species of origin for each cell) from GEO: https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE23640039. The cell type and other metadata were shared by the original authors of the study.

Parathyroid_Fig6H.ipynb was used to do the analysis and figure making related to the adult parathyroid data from chimeras.  The files containing TPM estimates for each mouse transcript were downloaded from GEO: https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE232600

Finally, Making_Tables.ipynb was used to collate supplemental tables 1-3.
