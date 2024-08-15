# singleCellAnalysis
A collection of software for analyzing single-cell data sets.

## Bartelt et al., 2024
Software used to analyze snRNA-seq data sets from Bartelt et al. 2024 is available in the directory 2024BarteltEtAl.  There are three files numbered 00 through 02.  These files are sequential and will take the user from CellRanger output, to filtered and annotated Seurat objects, and include details for subclustering analysis as well as our pseudobulk DEseq2 differential expression approach. There are places where the user may need to modify the code based on their computer system, version of R or Seurat, and whether they are processing the 5 week, 8 week, or human data sets; these locations in the code are marked with comments.

- The first file, 00_Preprocessing_MULTIseq, begins with CellRanger filtered_feature_barcode_matrix output, extracts cell barcodes, utilizes the MULTIseq deMULTIplex software to match cell barcodes to oligo barcodes from MULTIseq fastq files, and annotates the Seurat file with metadata. Cell type identification and annotation also takes place in this file. Note: the deMULTIplex step will likely need to be run on a compute cluster.
- The second file, 01_Seurat_Analysis, uses the filtered and annotated Seurat file to calculate useful QC metrics, investigate disease signals, and perform cell type subclustering analyses.
- The third file, 02_Pseudobulk_DEseq2, contains custom analysis code to extract raw counts for each cell type and each animal from the Seurat file, and uses the DEseq2 package to calculate DEGs, taking into account biological replicates, and raw read count differences between control and SCA7 animals.

