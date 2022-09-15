# Combination of point-feature learning networks and Imitation&Reinforcement learning
This work is inspired from this paper ([CVPR 2021](https://openaccess.thecvf.com/content/CVPR2021/html/Bauer_ReAgent_Point_Cloud_Registration_Using_Imitation_and_Reinforcement_Learning_CVPR_2021_paper.html), [arXiv](https://arxiv.org/abs/2103.15231)).

There are three model running using GoogleColab supported.
- Model1: DGCNN + ReAgent model
- Model2: PointNet++ ReAgent model
- Model3: "Deep Matching" module + ReAgent - try to increase the accuracy in case of partial overlapped point clouds

## Datasets and Pretrained Models

### ModelNet40
Point clouds sampled from ModelNet40 models can be downloaded [here](https://shapenet.cs.stanford.edu/media/modelnet40_ply_hdf5_2048.zip).
Extract the dataset and set the `M40_PATH` accordingly in `config.py`.

You can also find the downloaded dataset in folder _/data_ and the code running in _/dataset_



### Pretrained models
Weights for all training model can be found in _/weights/.._

## Training
As just mentioned, for the experiments on ModelNet40, we train a single model on the first 20 categories of ModelNet40 in a two-step process. First, we pretrain on noise-free samples using

`mode=pretrain`.
`dataset=m40`

Then, we finetune the model on noisy samples (as described in the paper). For this, use

`mode=MODE`,

where `MODE` is either IL-only (`il`) or IL+RL using the stepwise reward (`ilrl`).


## Evaluation

### ModelNet40
To compute the results for ModelNet40, run

`dataset=DATASET`,
`mode=MODE`,
`noise_type=TYPE`

with `DATASET` being either `m40-model` (first 20 categories, test split), `m40-cat` (last 20, test split). MODE can be `il`, `ilrl`. `TYPE` can be `clean`, `jitter` (noisy case) or `crop` (partial case)



## Citation
From this repository:

```
@article{bauer2021reagent,
    title={ReAgent: Point Cloud Registration using Imitation and Reinforcement Learning},
    author={Bauer, Dominik and Patten, Timothy and Vincze, Markus},
    booktitle={IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
    month={June},
    year={2021},
    pages={14586-14594}
}
```
