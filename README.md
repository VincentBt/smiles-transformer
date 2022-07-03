# SMILES Transformer

[SMILES Transformer](http://arxiv.org/abs/1911.04738) extracts molecular fingerprints from string representations of chemical molecules.  
The transformer learns latent representation that is useful for various downstream tasks through autoencoding task.

## Requirement
This project requires the following libraries.

- NumPy
- Pandas
- PyTorch > 1.2
- tqdm
- RDKit

## Dataset
Canonical SMILES of 1.7 million molecules that have no more than 100 characters from Chembl24 dataset were used.  
These canonical SMILES were transformed randomly every epoch with [SMILES-enumeration](https://github.com/EBjerrum/SMILES-enumeration) by E. J. Bjerrum.  

## Pre-training
After preparing the SMILES corpus for pre-training, run:

```
$ python pretrain_trfm.py
```

Pre-trained model is [here](https://drive.google.com/file/d/1LwE2BzvtDaPGYv0OR6iBjmsqoloH885N/view?usp=sharing).

## How to actually use Transformer pre-trained model

The downloadable pre-trained model is not enough to launch files in folder Experiments: vocab.pkl is missing.
Generate vocab.pkl as explained (for more details, see [here](https://github.com/DSPsleeporg/smiles-transformer/issues/17#issuecomment-947417504)):
- Download chemble_24_1_chemreps.txt.gz and extract it as chemble_24_1_chemreps.txt
- Run prepare_data.ipynb to create chemble_24.csv
- Run build_corpus.py to create chemble24_corpus.txt
- Run build_vocab.py to create vocab.pkl

Note that recovering RNNSeq2Seq pre-trained model is not possible easily, because the file seq2seq_1.pkl is missing (one would need to do the pre-training from scratch, contrary to above).

## Downstream Tasks
See `experiments/` for the example codes.

Note that data files associated to the experiments are not present, so the code cannot be executed.

## Cite
```
@article{honda2019smiles,
    title={SMILES Transformer: Pre-trained Molecular Fingerprint for Low Data Drug Discovery},
    author={Shion Honda and Shoi Shi and Hiroki R. Ueda},
    year={2019},
    eprint={1911.04738},
    archivePrefix={arXiv},
    primaryClass={cs.LG}
}
```
