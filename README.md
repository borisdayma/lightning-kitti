# Lightning Kitti

*Semantic Segmentation with Pytorch-Lightning*

## Introduction

This is a simple demo for performing semantic segmentation on the [Kitti dataset](http://www.cvlibs.net/datasets/kitti/eval_semseg.php) using [Pytorch-Lightning](https://pytorch-lightning.readthedocs.io/) and optimizing the neural network by monitoring and comparing runs with [Weights & Biases](https://docs.wandb.com/).

Pytorch-Ligthning includes a logger for W&B that can be called simply with:

```python
from pytorch_lightning.loggers import WandbLogger
from pytorch_lightning import Trainer

wandb_logger = WandbLogger()
trainer = Trainer(logger=wandb_logger)
```

Refer to [the documentation](https://docs.wandb.com/library/frameworks/pytorch/lightning) for more details.

Hyper-parameters can be defined manually and every run is automatically logged onto [Weights & Biases](https://www.wandb.com/) for easier analysis/interpretation of results and how to optimize the architecture.

You can also run [sweeps](https://docs.wandb.com/sweeps/) to optimize automatically hyper-parameters.

*Note*: this example has been adapted from Pytorch-Lightning examples.

## Usage

### Notebook

- A quick way to run the training scrip is to go to the `notebook/tutorial.ipynb` and play with it.

### Script

1. Clone this repository.
2. Download [Kitti dataset](http://www.cvlibs.net/datasets/kitti/eval_semseg.php)
3. The dataset will be downloaded in the form of a zip file namely `data_semantics.zip`. Unzip the dataset inside the `lightning-kitti/data_semantic/` folder.
4. Install dependencies through `requirements.txt`, `Pipfile` or manually (Pytorch, Pytorch-Lightning & Wandb)
5. Log in or sign up for an account -> `wandb login`
6. Run `python train.py` and add any optional args
7. Visualize and compare your runs through generated link

   ![alt text](imgs/results.png)

## Sweeps for hyper-parameter tuning

[W&B Sweeps](https://docs.wandb.com/sweeps/) can be defined in multiple ways:

* with a YAML file - best for distributed sweeps and runs from command line
* with a Python object - best for notebooks

In this project we use a YAML file. You can refer to [W&B documentation](https://docs.wandb.com/library/integrations/lightning) for more Pytorch-Lightning examples.

1. Run `wandb sweep sweep.yaml`
2. Run `wandb agent <sweep_id>` where `<sweep_id>` is given by previous command
3. Visualize and compare the sweep runs

   ![alt text](imgs/sweep.png)

## Results

After running the script a few times, you will be able to compare quickly a large combination of hyperparameters.

Feel free to modify the script and define your own hyperparameters.

[See the live report → ](https://app.wandb.ai/borisd13/lightning-kitti/reports/Lightning-Kitti--Vmlldzo3MTcyMw)
