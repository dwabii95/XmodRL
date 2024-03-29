# XmodRL
Explainable Modular Reinforcement Learning (from images)

## What is happening here?

TODO: Insert image of task splitting

This repository contains a modular reinforcement learning framework. Instead of using one algorithm for the whole reinforcement learning task, this framework gives the possibility to choose specific solver for subtasks of a reinforcement learning problem. The three subtasks are the following:

1. Extracting raw features
2. Processing them to meaningful features
3. Generating a policy from meaninful features

## How to simple call

Pretrained models and their config files are available inside ```pretrained/```. To use one of the pretrained models:

```
sh setup_pretrained.sh
cd src

# for just evaluating a trained model
python xrl.py --config ../pretrained/configs/pretrained-boxing-gen.yaml mode eval 

# for creating a video while evaluating a trained model
python xrl.py --config ../pretrained/configs/pretrained-boxing-gen.yaml mode eval make_video True   

# for showing the liveplot while using a trained model
python xrl.py --config ../pretrained/configs/pretrained-boxing-gen.yaml mode eval liveplot True
```

There are other example config files inside `configs`-Folder for various experiments. They can be used to train new models. 

## A little deeper explanation about the framework

The main file to call in this framework is `src/xrl.py`. It is called together with a path to a config file. The structure of the config files are defined in `src/xrl/xrl_config.py`. A config file configures the Atari-Game, the selected algorithms and methods for the modular blocks and other training parameters. 

Parameters set in the config file can be overwritten by calling the parameter and its new value in the command. For example: 

```
python src/xrl.py --config path/to/config/file.yaml device "cpu"
```

This call overwrites the "device"-parameter to "cpu"

TODO: Checkpoint and logs
