## Steps
Go to [Getex](https://gtexportal.org/home/downloads/nhp-dgtex) website and download the NHP-dGTEx_Marmoset_Analysis_2025-08-08_v1_RNASeQCv2.4.3_gene_tpm.gct.gz in TPM.

TPM is used by Borzoi because thereś length normalization (allows for fair comparison of short and long genes) and depth normalization (ensures comparable values ​​across different samples in your species)

Borzoi is a model trained primarily on human data. By comparing it to the Marmoset .gct, we validate whether the AI ​​is capable of accurately predicting a different species. If the Borzoi and .gct numbers move in the same direction, it means the model is able to understand the marmoset genome.

So, this .gct will be used to validate whether the results predicted by Borzoi are proportional to what is observed in the laboratory, to compare the prediction that borzoi will do.

We explored the contents of the .gct file to understand gene nomenclature. We identified that the Marmoset data contains two types of identifiers:

- Ensembl (ENSCJAG-type IDs...)

- NCBI (LOC-type IDs...)

### Ensembl
Before analyzing specific genes, we need the complete "map" of the species. To obtain this, we downloaded the global files for all Marmoset genes from the official databases ([Ensembl](https://www.ensembl.org/Callithrix_jacchus/Info/Index)):

- FASTA file: Contains the complete DNA sequence of all chromosomes of the species. We chose the dna_sm (Soft-Masked) version so that the model could correctly identify repetitive regions.

- GTF file: This is the annotation dictionary containing the exact coordinates (start, end, chromosome, and strand) of each of the known genes of the species.


We start predicting one Ensembl gene PLCXD1(ENSCJAG00000083719):

We created an index that allows the model to instantly "jump" to any position in the DNA without having to read the entire gigabyte file.

`samtools faidx Callithrix_jacchus.mCalJac1.pat.X.dna_sm.toplevel.fa`

**1) ENSCJAG00000083719**
   
To find out which coordinates to request from the index, we use this command to filter the gtf annotation file:

`zgrep "ENSCJAG00000083719" Callithrix_jacchus.mCalJac1.pat.X.115.gtf.gz | awk '$3=="gene"'`

We obtain the following result: 

        Callithrix_jacchus.mCalJac1.pat.X.115.gtf.gz | awk '$3=="gene"'
        Y	ensembl	gene	81486	108918	.	+	.	gene_id "ENSCJAG00000083719"; gene_version "1"; gene_name "PLCXD1"; gene_source "ensembl"; gene_biotype "protein_coding";

It is located on the Y chromosome (81,486 - 108,918)

Now we can do our prediction on the borzoi. Here's the code(prueba 5PONEEEEEEEEEEEEEEEEEER)

Then we have to compare the results obtained in the borzoi prediction with the gct values


**2) ENSCJAG00000071157**

To find out which coordinates to request from the index, we use this command to filter the gtf annotation file:

`zgrep "ENSCJAG00000071157" Callithrix_jacchus.mCalJac1.pat.X.115.gtf.gz | awk '$3=="gene"'`

We obtain the following result: 

        Callithrix_jacchus.mCalJac1.pat.X.115.gtf.gz | awk '$3=="gene"'
        Y	ensembl	gene	138951	141749	.	-	.	gene_id "ENSCJAG00000071157"; gene_version "1"; gene_source "ensembl"; gene_biotype "lncRNA";

It is located on the Y chromosome (138,951 - 141,749)

Now we can do our prediction on the borzoi. Here's the code(prueba6 PONEEEEEEEEEEEEEEEEEER)

Then we have to compare the results obtained in the borzoi prediction with the gct values








1) ENSCJAG00000083719
==================================================================================================
Total params: 185917723 (709.22 MB)
Trainable params: 185892699 (709.12 MB)
Non-trainable params: 25024 (97.75 KB)
__________________________________________________________________________________________________
None
model_strides [32, 32]
target_lengths [6144, 6144]
target_crops [5120, 5120]

📊 RESULTADOS CUANTITATIVOS (PRUEBA 5)
🧬 Gen: PLCXD1
🔮 Suma de la montaña (Borzoi): 49.1498
🧪 Valor real (.gct):           1.6112
---------------------------------------------
✅ Factor de proporcionalidad: 30.51
=============================================

2) ENSCJAG00000071157
==================================================================================================
Total params: 185917723 (709.22 MB)
Trainable params: 185892699 (709.12 MB)
Non-trainable params: 25024 (97.75 KB)
__________________________________________________________________________________________________
None
model_strides [32, 32]
target_lengths [6144, 6144]
target_crops [5120, 5120]

📊 RESULTADOS CUANTITATIVOS (GEN 2)
🧬 Gen: lncRNA (ENSCJAG00000071157)
🔮 Suma de la montaña (Borzoi): 225.7202
🧪 Valor real (.gct):           0.0168
---------------------------------------------
✅ Factor de proporcionalidad: 13435.73
=============================================









