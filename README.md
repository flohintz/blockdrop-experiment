# blockdrop-experiment

## Blockdrop extension: 

This code is an addition and modification of the original implementation of BlockDrop (https://github.com/Tushar-N/blockdrop) and is part of the article "How to improve your deep learning performance using BlockDrop". 

The goal of this implementation was to find out when BlockDrop is benefitial in comparison to a sole ResNet.
To do so, the following steps were done:
1. Bring BlockDrop up-to-date (Python2 --> Python 3) and comment the code 
2. Add a notebook which combines training of the Policy Network and the Joint finetung and measures the time of the training
3. Add an additiona script which measures the time of inference
4. Implement a sole ResNet, which is used as comparison to blockdrop

## Steps of BlockDrop and the name of the notebooks (in brackets: where to find pretrained versions to start at this step)
1. train Policy Net and finetuning --> ```blockdrop_training.ipynb``` (input: cv/trained_rnet)
2. Inference of BlockDrop  --> ```blockdrop_inference.ipynb``` (input: cv/finetuned)

Both implementations are based on the original BlockDrop implementation, but are heavily adjusted.

### How to use BlockDrop: 
The usage of BlockDrop can be started at all various steps, since pretrained versions after all of the four steps were saved and are available in the code. 
The pretrained versions can be found under cv/. There are different pretrained versions available (e.g. ResNets with different depths)

Since there are different pretrained models available, the following list describes, which is used as "standard" version for each of the notebooks. All of them are also available in the original BlockDrop implementation.

train Policy Net: cv/trained_rnet/R110_C10/pk_E_130_A_0.932.t7

Joint finetuning of Policy and ResNet: cv/trained_policy/R110_C10/ckpt_E_100.t7

Inference: cv/finetuned/R110_C10/ckpt_E_2000_A_0.936_R_1.95E-01_S_16.93_#_469.t7

## Run the notebook:
In contrast to the original BlockDrop implementation, the notebook can directly be run without adding variables to the input.
This is the case as all variables are included within the notebook in this implementation. The variables can also be changed directly within the notebook.

## The experiment:
For the experiment, BlockDrop is compared to a sole ResNet on the dataset ```CIFAR10```. To do so, the following notebooks were created:

```rnet_sole.ipynb```: creating an own ResNet implementation to compare it to BlockDrop --> includes both training and testing

```blockdrop_training.ipynb```: executes the Policy Net training and joint finetuning and measures the time in seconds for later comparision

```blockdrop_inference.ipynb```: a simplified testing script (compared to original BlockDrop test script) to have similar conditions for the testing of both, BlockDrop and the sole ResNet

The results of the experiment can be read in the article "How to improve your deep learning performance using BlockDrop".

