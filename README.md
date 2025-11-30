# ML_CellClassification
Intro:

Acute myeloid leukemia (AML) is a very heterogeneous disease. There are many different forms of the disease depending on the patient mutation. The smallest change in mutation will render it either a different form of leukemia or even another form of AML. These changes also determine the treatment as well, with different drugs and combinations affecting each cell a different way depending on the mutation status of the patient. To understand the mutation that a patient holds and the effects it has on their system a robust sequencing method like cite-seq is preferred to improve the efficacy of categorization and cell identification. In our experiment we have patients with varying stages and mutation patterns whose cells will undergo 7 different treatments to understand the effect these treatments have on separate cell populations in differently mutated patients. 


Steps in process

Download any packages necessary for script (usually manually indicated by "import"). You'll most likely have to "pip install" install of conda install. It is still nice to have a conda environment to do all of this in.  

Convert seurat object to anndata object using "Convert_Seurat_Anndata.rmd"

(Export data from BMM objects to have as reference in preprocessing)

Merging all the bulk and sc RNA-seq count data into an object

Preprocessing each dataset

Integrate them together (I used Scanorama for this which seems to work okay but there are lots of options)

Iterating over the mutation gene data in the mutations file, determining if there are enough samples of that mutation to train a model (cutoff is 10 samples), if so, I'm taking that amount times 2 of "normal" or samples without that mutation and using those as "no mutation" samples

Training models using each of these mutation groups and matching their identifiers to the RNA counts using the mutant samples as positive and the non-mutant for that gene as negative in each model

Applying those models to the scRNA integrated data OR if I didn't integrate the data.

