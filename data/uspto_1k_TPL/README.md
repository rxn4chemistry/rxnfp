# USPTO 1k TPL

We introduce a new data set for chemical reaction classification called USPTO 1k TPL (TPL for TempPLates). USPTO 1k TPL is derived from the [USPTO data base](https://figshare.com/articles/Chemical_reactions_from_US_patents_1976-Sep2016_/5104873) by Lowe. It consists of 445k reactions divided into 1000 template labels. We split the data set randomly into train/valid 90% and test 10%. 

The reaction labels were obtained by atom-mapping the USPTO data set with [RXNMapper](http://rxnmapper.ai), then applying the [template extraction workflow](https://github.com/reymond-group/CASP-and-dataset-performance) by Thakkar et al. and finally, selecting reactions belonging to the 1000 most frequent template hashes. Those template hashes were taken as class labels. Similarly to the Pistachio class data set, USPTO 1k TPL is strongly imbalanced.

The full data set, together with computed reaction fingerprints and confusion matrices, can be downloaded from: [MappingChemicalReactions](https://ibm.box.com/v/MappingChemicalReactions). 