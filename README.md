# Augmenting genetic algorithms with deep neural networks for exploring the chemical space
This repository contains code for the paper: [Augmenting genetic algorithms with deep neural networks for exploring the chemical space](https://arxiv.org/abs/1909.11655). 



Here is a visualization of molecular progress: 

<img align="center" src="./readme_docs/mol_view.gif"/>

## Prerequisites
For cloning the repository, please have a look at the Branch Navigator section.  

Before running the code, please ensure you have the following:
- [SELFIES (any version)](https://github.com/aspuru-guzik-group/selfies) - 
  The code was run with v0.1.1 (which is the fastest), however, the code is compatible with any version. 
- [RDKit](https://www.rdkit.org/docs/Install.html)
- [tensorboardX](https://pypi.org/project/tensorboardX/)
- [Pytorch v0.4.1](https://pytorch.org/)
- [Python 3.0 or up](https://www.python.org/download/releases/3.0/)
- [numpy](https://pypi.org/project/numpy/)

Please note: that the Synthetic Accesability calculater (i.e. directory SAS_calculator) comes from - [ https://github.com/EricTing/SAscore]( https://github.com/EricTing/SAscore).


## How to run the code? : 
We highly recommend using the following version for running your experiments.  
```
python ./core_GA.py
```  

The following settings can be customized (found at the end of the file 'core_GA.py'): 
- num_generations: Number of generations to run the GA
- generation_size: Molecular population size encountered in each generation 
- starting_selfies: Initial population of molecules 
- max_molecules_len: Length of the largest molecule string
- disc_epochs_per_generation: Number of epochs of training the discriminator neural network 
- disc_enc_type: Type of molecular encoding shown to the discriminator
- disc_layers : Discriminator architecture
- training_start_gen: generation after which discriminator training begins 
- device: Device the discriminator is trained on 
- properties_calc_ls: Property evaluations to be completed for each molecule of the GA
- num_processors: Number of cpu cores to parallelize calculations over
- beta: Value of parameter beta
- impose_time_adapted_pen: Boolean variable to indicated use of a time-adapted discriminator penalty

## How are the results saved?  : 
All the results are savents in the 'results' directory. Our results are saved as (Note: 'i' is the run iteration): 
1. images_generation_0_i:  
   Images of the top 100 molecules of each generation. Below each molecule are the Fitness, logP, SA, ring penalty and discriminator scores
2. results_0_i:  
   Each sub-directory is named by the generation. The smile strings (ordered by fitness) and corresponding molecular properties are provided as text
   files: 'smiles_ordered.txt', 'logP_ordered.txt', 'sas_ordered.txt', 'ringP_ordered.txt', 'discrP_ordered.txt'. 
   Outside the sub-directories is the information about the best molecules of a generation. 
3. saved_models_0_i:  
   The trained discriminators after each generation. Please Note: We did not make use of the discriminator predictions in the Fitness for this experiment (beta is set to 0).



