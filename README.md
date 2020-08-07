# RXNFP - chemical reaction fingerprints
> This library generates chemical reaction fingerprints from reaction SMILES


## Install


For all installations, we recommend using `conda` to get the necessary `rdkit` and `tmap` dependencies:

### From pypi

```console
conda create -n rxnfp python=3.6 -y
conda activate rxnfp
conda install -c rdkit rdkit
conda install -c tmap tmap
pip install rxnfp
```


### From github
```console
conda create -n rxnfp python=3.6 -y
conda activate rxnfp
conda install -c rdkit rdkit
conda install -c tmap tmap
pip install -e .
```

## How to use

Compute a fingerprint from a reaction SMILES
```python
```

```
from rxnfp.transformer_fingerprints import (
    RXNBERTFingerprintGenerator, get_default_model_and_tokenizer, generate_fingerprints
)

model, tokenizer = get_default_model_and_tokenizer()

rxnfp_generator = RXNBERTFingerprintGenerator(model, tokenizer)

example_rxn = "Nc1cccc2cnccc12.O=C(O)c1cc([N+](=O)[O-])c(Sc2c(Cl)cncc2Cl)s1>>O=C(Nc1cccc2cnccc12)c1cc([N+](=O)[O-])c(Sc2c(Cl)cncc2Cl)s1"

fp = rxnfp_generator.convert(example_rxn)
print(len(fp))
print(fp[:5])
```

    256
    [-2.0174953937530518, 1.7602033615112305, -1.3323537111282349, -1.1095019578933716, 1.2254549264907837]


Or for a list of reactions:

```
rxns = [example_rxn, example_rxn]
fps = rxnfp_generator.convert_batch(rxns)
print(len(fps), len(fps[0]))
```

    2 256


## Reaction Atlas

### Pistachio
The fingerprints can be used to map the space of chemical reactions:



<div style="text-align: center">
<img src="nbs/images/annotated_atlas.jpg" width="1000">
<p style="text-align: center;"> <b>Figure:</b> Annotated Atlas of the Pistachio test set generated with TMAP (https://tmap.gdb.tools). </p>
</div>


### Schneider 50k set

In the notebooks, we show how to generate an interative reaction atlas for the Schneider 50k set. The end result is similar to this **[interactive Reaction Atlas](https://rxn4chemistry.github.io/rxnfp//tmaps/tmap_ft_10k.html)**.

Where you will find different reaction properties highlighted in the different layers:

<div style="text-align: center">
<img src="nbs/images/tmap_properties.jpg" width="800">
<p style="text-align: center;"> <b>Figure:</b> Reaction atlas of 50k data set with different properties highlighted. </p>
</div>

## Citation 

Our work was first presented in the NeurIPS 2019 workshop for [Machine Learning and the Physical Sciences](https://ml4physicalsciences.github.io), the most recent version can be found on [ChemRxiv](https://chemrxiv.org/articles/Data-Driven_Chemical_Reaction_Classification_with_Attention-Based_Neural_Networks/9897365

```
@article{Schwaller2019rxnfp,
author = "Philippe Schwaller and Daniel Probst and Alain C. Vaucher and Vishnu H Nair and David Kreutter and Teodoro Laino and Jean-Louis Reymond",
title = "{Mapping the Space of Chemical Reactions using Attention-Based Neural Networks}",
year = "2019",
month = "9",
url = "https://chemrxiv.org/articles/preprint/Data-Driven_Chemical_Reaction_Classification_with_Attention-Based_Neural_Networks/9897365",
doi = "10.26434/chemrxiv.9897365.v3"
}
```

RXNFP has been developed in a collaboration between IBM Research Europe and the [Reymond group](http://gdb.unibe.ch) at the University of Bern. The classification models are used on the [RXN for Chemistry](https://rxn.res.ibm.com) platform.
