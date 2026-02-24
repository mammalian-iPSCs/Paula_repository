# Borzoi
Is a model that learns to predict cell-type-specific and tissue-specific RNA-seq coverage from DNA sequence.
They isolate and accurately score DNA variant effects across multiple layers of regulation, including transcription, splicing and polyadenylation
They extract cis-regulatory motifs driving RNA expression and post-transcriptional regulation in normal tissues.

Until now, AI models were like nearsighted people. They could see a letter up close, but they didn't understand how a letter on page 1 of a book affected what happened on page 50. Furthermore, almost no model could predict RNA-seq (which is the ultimate test of how much "fuel" or expression a gene has).
Enter Borzoi's architecture, capable of processing sequences up to 524 kb with a resolution of 32 bp.
It not only tells you if the gene is switched on, but it predicts the entire map: where the gene starts, how the excess pieces are cut off (splicing), and where it ends.

## Borzoi parts
- Convolutions: These are like magnifying glasses that scan the DNA, searching for short "words" or puzzle pieces (the motifs). For example, they look for the sequence where the Yamanaka factor attaches.
- Transformers: This allows the AI ​​to remember what it read at the beginning of the sequence and relate it to the end. It's what allows Borzoi to understand that a "switch" (enhancer) that is very far away can activate a gene. This is vital for your Yamanaka factors, because their "on buttons" are often very far from the main gene.

## RNA-seq
RNA-seq measures gene expression. While almost all your cells have the same DNA, not all of them "read" the same instructions. RNA-seq captures that exact moment and tells you which genes are active and how many copies of their message (mRNA) have been made.
1) Capture: All the RNA is extracted from a sample (for example, a stem cell you are reprogramming).
2) Conversion: Because RNA is very fragile, it is converted into complementary DNA (cDNA) so it can be read.
3) Sequencing: A machine reads the sequences of those "photocopies" and generates millions of tiny fragments of text.
4) Mapping: A computer aligns those fragments with the original genome to see which gene they came from.
5) Counting: If one gene has 1,000 fragments attached and another has 10, you know the first one is much more active.

## Borzoi Results
The researchers didn't just see if the model was right about what it already knew. They tested Borzoi with DNA it had never seen. They wanted to check if, just by reading the sequence of letters (A, C, G, T), the model was able to draw the "mountains" of expression that we would see in a real laboratory experiment (prediction = it has learned the universal rules of how genes are activated).
Borzoi learned from humans and mice, but since the Yamanaka factors are almost identical in all animals, the predictions about them should be quite good even though we are looking at a distant species.

**How will Borzoi be evaluated?**

- Pearson correlation (r): This is a number that indicates how closely the prediction matches reality. If it is 1.0, it is perfect; if it is 0, it is pure chance. A drop in the Pearson correlation coefficient will mathematically indicate the extent to which the model "understands" the regulation of that species.
- Coverage Prediction: The model attempts to predict how many "photocopies" (RNA reads) will be present in each small section of the genome.
- Other values ​​include Z-scores and AUPRC.

**FIGURES**

Fig. 1a) The model receives a 524 kb DNA sequence, uses a mixture of "filters" (convolutions) to see details and "memory" (transformers) to understand long distances. Borzoi doesn't give you a single number, but rather draws "tracks." Imagine that for each tissue (heart, liver, etc.), the model draws a line that goes up and down indicating how much RNA activity there is at each point. Unlike others, Borzoi predicts the complete RNA-seq, including the gaps where there are no exons.

Fig. 1b) Compare what Borzoi predicted with what was actually observed in the laboratory. The authors show how the model is almost perfect at identifying where the exons (the parts of the gene that are used) and the introns (the parts that are discarded) are.

Here they use graphs called "scatter plots" to give the model a final grade: each point on the graph represents a gene, forming a perfect diagonal line, which means the AI ​​is an expert. Borzoi demonstrates a very high correlation (close to 0.8 or 0.9 in many cases), which means its "predictions" are very close to biological reality.

Fig. 2a) The "Cut and Paste" (Splicing) Challenge: The model demonstrates its ability to predict where RNA is cut to join exons, even though it was never trained by explicitly telling it "here's a cut site." It learned this simply by observing the sequence and comparing it to the "mountains" of the RNA sequence (mountains = exons). Because the prediction and reality match almost perfectly, the authors conclude that the model understands where to cut the RNA even without explicit instruction. Alternative Splicing: The model predicts when a cell chooses to use "Exon A" and when it prefers "Exon B." This is crucial for Yamanaka factors, as some versions of these proteins function while others do not.

Fig. 2c) Borzoi changes its prediction depending on the sequence and type of tissue it is simulating.

---

**QTL**: A QTL is a region associated with variation in a specific trait. For example, if the thickness of a mammal's hair changes depending on a letter in its DNA, that region is a QTL.

**eQTL**: An eQTL is a specific type of QTL. Here, the "trait" that changes isn't something you can see with the naked eye (like eye color), but rather the amount of RNA a gene produces (causing a gene to be expressed more strongly or weakly). "If I change this letter, will the amount of RNA change?"

In our study, we used Borzoi to predict whether genomic differences between species act as eQTLs, altering the amount of messenger RNA produced by pluripotency factors.

Borzoi specializes in predicting these eQTLs directly from the sequence, guessing whether a mutation will increase or decrease the "volume" of a Yamanaka factor.
___

Fig. 3: Borzoi not only understands "healthy" DNA, but can also predict what happens when there is a mutation (eQTL).
Fig. 3a) Borzoi predicts whether a mutation switches a gene on or off.
If you give Borzoi the sequence of a lion with a mutation, the model will tell you with considerable accuracy whether that gene will be expressed more or less than in humans.
Borzoi can understand mutations that are very far from the gene, something that "short-sighted" models don't grasp. It is capable of predicting that a single changed letter can cause an entire piece of protein to disappear (exon skipping).

This is fundamental for our project: if the lion's Yamanaka factor has a mutation there, Borzoi will warn you that the resulting protein will be different.

Fig. 4 Borzoi demonstrates its ability to locate TFBSs using saliency scores and motifs.

Fig. 4a) Borzoi identifies which letters are the most important (the large ones) for a gene to be activated. The authors demonstrate that these letters exactly match the motifs of known transcription factors. For your project, this means that Borzoi can "draw" the socket where OCT4 or SOX2 connects simply by reading the DNA of the lion or human. Borzoi explains why a variant is an eQTL. The model identifies that the variant has broken a motif (a TFBS) where a protein should bind. When this "socket" is broken, gene expression drops. Borzoi visualizes this using saliency scores.

Fig. 4b) The model understands how TFBSs control expression. Here, they compare the strength with which a factor binds to DNA and how much "pile" of RNA it generates afterward.

This allows us to solve the distant species problem: even though the genome changes a lot between a human and a lion, if Borzoi keeps finding the conserved motif of pluripotency factors in the same place, we can assume that the regulation is still working. It's proof that the model understands the 'grammar' of transcription factors.



## CONCLUSION

### Benefits

Borzoi, a unified model capable of predicting end-to-end RNA regulation (transcription, splicing, and polyadenylation) using only the DNA sequence. By processing 524 kb, the model captures the communication between promoters and enhancers that are far apart, something previous models did not do well.

By examining two distinct genomes, the model learned that there are "universal rules" that have held true after millions of years of evolution. This reinforces your theory that the highly conserved motifs of the Yamanaka factors will be well predicted even in the lion.

Borzoi is a powerful tool for prioritizing disease-causing variants that alter the expression of pluripotent genes (eQTL). We can use it as a "filter" to see which cross-species mutations are truly important and which are merely evolutionary "noise."
Success Metric: Establishing a correlation between the predicted saliency scores (motifs) and the actual RNA-seq/ATAC-seq data to define the phylogenetic boundary of the model (Does it work in the lion?).

### Disadvantages

- Distance Limit: Although it sees 524 kb, if a switch is more than 1 Mb away (as happens in some complex genes), Borzoi becomes "blind" to that signal. This is where AlphaGenome could help, as it reaches 1 Mb.

- Resolution: Remember that Borzoi works in 32 bp blocks. The authors admit that to see minute details of a single letter, higher-resolution models are necessary. (Use AlphaGenome for this part)

- Indirect effects: The model is very good at predicting what is written in the DNA ("cis"), but it cannot tell if there is an external signal in the cell (such as a hormone or a drug) that changes the entire system


## Future methodology to apply

- Sequence files (DNA) from 50 species in FASTA format

- 524,288 bp window centered on the gene we want to study (Yamanaka factors)

- Transform the sequences to TRRecord, a binary format that allows the AI ​​to read the data very quickly.

- Prepare the configuration file so that Borzoi knows you want an RNA-seq prediction for that region.


## Methods explained in the Borzoi's paper

### Data preparation

- Sources: They used thousands of RNA-seq experiments from humans (from the GTEx project) and mice.

- The DNA: They divided the genome into overlapping fragments of 524,288 letters (524 kb). This is what you will have to do with the lion or gorilla genome to give it to Borzoi.

- Targets: The scientists processed the RNA-seq data to create "tracks" that indicate how many reads are in each 32-letter (32 bp) block of the genome.


### Model architecture

- Convolutional Narrow Layers (CNNs): These function as local scanners that detect motifs (like those in OCT4).

- Transformer blocks: These allow the model to "remember" an enhancer that is 400 kb away from the gene and understand that it is a distal eQTL.

- Multitasking output: The model does not only predict RNA-seq; It also predicts ATAC-seq and histone marks simultaneously to help better understand the context.


### Training strategy (Borzoi didn't learn everything at once; it had a learning strategy)

- Poisson loss: They use a specific mathematical formula to compare how many reads the model predicts versus how many actually occurred.

- Multispecies training: They trained the model with human and mouse data simultaneously. This is what allows the model to be robust across species B, because it learned to ignore the "noise" and focus on universal genomic rules.

### Variant Effect Prediction - eQTLs
- eQTL calculation: To determine if a letter is an eQTL, the model reads the original sequence and then the sequence with the mutation.

- Prediction difference: If the expression "bump" changes between the two sequences, Borzoi marks that letter as a functional eQTL.

- Saliency Scores: These calculate gradients to pinpoint the exact nucleotide responsible for the change in expression, thus visualizing the affected motif.


### Splicing and APA Analysis

- Splicing Metrics: These define metrics such as PSI (Percent Spliced ​​In) to quantify what percentage of transcripts include a given exon.

- sQTL Mapping: This evaluates how genetic variants affect RNA "cut and paste," allowing prediction of whether a mutation in a species will destroy the resulting protein.



















