# ProteinNetworks

In this project I compared different types of neural network architectures in classification tasks. Task1 was a binary classification, Task2 was a multiclass classification. The datasets I used are:

- Dataset1 (Notebook1): 14000 enzyme sequences that belong to 7 classes of enzymes and 14000 protein sequences of non-enzymes. All of the sequences are of length 600-1000 and belong to vertebrates.
- Dataset2 (Notebook2): 5000 enzyme sequences that belong to 5 subclasses of ligases and 5000 protein sequences of non-enzymes. All of the sequences are of length 600-1000 and belong to vertebrates.
- Dataset3 (Notebook3) (only multiclass classification): protein sequences of proteins that locate themself in Nucleus, Cell Membrane and Extracellular space. 290 sequences of each class - a subset of Wei et. al. 4802 dataset.

The three architectures I implemented to work on the data are:

- FFNN with no convolution.
- CNN with one layer of convolution.
- CNN with five stacked layers of convolution.

I also took two approaches to providing an input data to my networks. 

- Input data one - a protein encoded as an array with a pI score centered at 0 (pI = 7 -> 0) for each amino acid in a sequence.
- Input data two - 28 physico-chemical parameters of a sequence created with ProtParam EMBOSS package.

To set the final parameters of the networks and determine an optimal way to pad sequences for given tasks, FFNN with no convolution network was used:

<img src="https://github.com/szymonszrajer/ProteinNetworks/blob/main/images/pad.png" width="800" height="400">

Middle padding was chosen for the sequences provided as input data one.

The result for above description (Dataset 1&2, three network architectures with 2 input types for two tasks)are as follows:

![comparison](https://github.com/szymonszrajer/ProteinNetworks/blob/main/images/comparison.png "networks comparison")

Main tendencies that can be seen is that the models perform better with multiclass classification (when all of the sequences are enzymes and their class needs to be specified) and that the performance for the models is better on the smaller dataset - perhaps training for more epochs would've made networks perform better on Dataset1.

The below table provides a small insight to the tendencies mentioned above:

<img src="https://github.com/szymonszrajer/ProteinNetworks/blob/main/images/param.png" width="800" height="400">

Even though the tasks at hand are very similar, and the models architecture is the same, the performance is much better for a smaller dataset, indicating that number of parameters could be increased.

Additionaly, an attempt to combine best model architectures for different inputs was made:

<img src="https://github.com/szymonszrajer/ProteinNetworks/blob/main/images/combine2.png" width="700" height="500">

Combining architectures predictions yielded a decline in Task1 preformance and an improvement in Task2 performance.

When it comes to Dataset3, classifying location based on a sequence was unsuccessful, and assigning location based on physicochemical data was unsatisfactory ~60% accuracy for 3 class classification.

Bibliography:
- Lopez-del Rio, A., Martin, M., Perera-Lluna, A. et al. Effect of sequence padding on the performance of deep learning models in archaeal protein functional prediction. Sci Rep 10, 14634 (2020). https://doi.org/10.1038/s41598-020-71450-8
- Raj et al., J Proteomics Bioinform 2017, 10:12 DOI: 10.4172/jpb.1000459
- Jamal, S., Ali, W., Nagpal, P. et al. Predicting phosphorylation sites using machine learning by integrating the sequence, structure, and functional information of proteins. J Transl Med 19, 218 (2021). https://doi.org/10.1186/s12967-021-02851-0
- ElAbd, H., Bromberg, Y., Hoarfrost, A. et al. Amino acid encoding for deep learning applications. BMC Bioinformatics 21, 235 (2020). https://doi.org/10.1186/s12859-020-03546-x
- Yinan Shena, Jijun Tangab, Fei Guoa. Identification of protein subcellular localization via integrating evolutionary and physicochemical information into Chou’s general PseAAC. https://doi.org/10.1016/j.jtbi.2018.11.012
