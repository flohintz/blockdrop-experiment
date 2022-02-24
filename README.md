# blockdrop-experiment

## Testing of BlockDrop: 

This code is an addition and modification of the original implementation of BlockDrop (https://github.com/Tushar-N/blockdrop) and is part of the article "How to improve your deep learning performance using BlockDrop". 
The goal of this implementation was to find out when BlockDrop is benefitial in comparison to a sole ResNet.
To do so, the following steps were done:
1. Bring BlockDrop up-to-date (Python2 --> Python 3) and comment the code 
2. Add an additional script which measures the time of the training: blockdrop_training
3. Add an additiona script which measures the time of inference: blockdrop_test
4. Implement a sole ResNet, which is used as comparison to blockdrop: rnet_single

### BlockDrop Implementation:
As written before, the BlockDrop implementation is mainly based on https://github.com/Tushar-N/blockdrop and was only adapted for my experiment and for Python 3.

## Steps of BlockDrop and the name of the script (in brackets: where to find pretrained versions to start at this step)
1. train ResNet --> rnet_single.ipynb 
2. train Policy Net* --> policy_train.ipynb (input: cv/trained_rnet)
3. Joint finetuning of Policy and ResNet* --> finetuning.ipynb (input: cv/trained_policy)
4. Inference*  --> test.ipynb (input: cv/finetuned)

steps with a "*" are adjusted based on the original BlockDrop implementation. The others are completely implemented by myself.

### How to use BlockDrop: 
The usage of BlockDrop can be started at all various steps, since pretrained versions after all of the four steps were saved and are available in the code. 
The pretrained versions can be found under cv/. There are different pretrained versions available (e.g. ResNets with different depths)

Since there are different pretrained models available, the following list describes, which is used as "standard" version for each of the scripts. All of them are also available in the original BlockDrop implementation.

train Policy Net: cv/trained_rnet/R110_C10/pk_E_130_A_0.932.t7
Joint finetuning of Policy and ResNet: cv/trained_policy/R110_C10/ckpt_E_100.t7
Inference: cv/finetuned/R110_C10/ckpt_E_2000_A_0.936_R_1.95E-01_S_16.93_#_469.t7

## Run the scripts:
In contrast to the original BlockDrop implementation, the scripts can directly be run without adding variables to the input.
This is the case as all variables are included within the script in this implementation. The variables can accordingly be also changed directly within the script.

## The experiment:
For the experiment, BlockDrop is compared to a sole ResNet. For this, the following scripts were created:
```rnet_single.ipynb```: creating an own ResNet implementation to compare it to BlockDrop --> includes both training and testing
```blockdrop_training.ipynb```: executes the Policy Net training and joint finetuning and measures the time in seconds for later comparision

```blockdrop_test.ipynb```: a simplified testing script (compared to original BlockDrop test script) to have similar conditions for the testing of both, BlockDrop and the sole ResNet
As addition to this simplified testing, the pretrained ResNet of the original implementation was compared to BlockDrop using the original testing script: ```test.ipyn```
For the pretrained ResNet, the policy net was discarded and the input for the ResNet was simply set to 1 for the complete dropping vector. 

The result of the experiment can be read in the article xxxx.
In short:

