# Mars Lander with Reinforcement Learning

Environment for landing a rover on Mars. 

https://user-images.githubusercontent.com/17803473/159241507-2fe92a89-91c3-4f3e-aa34-8d2da1f6e567.mov

# Usage

Initialize with

```shell
python play.py
```

At each step, the program is expected two values separated by a space:
 - the change in rotation as an integer between -15 and 15
 - the change in thrust can take value -1, 0 and 1

A valid input would be `12 1`.

## Visualize environment

The command below will open a graphical window. It might not work if you use
a remote device or an online notebook (Google Colab, etc). The agent will
take random action.

```shell
PYTHONPATH=$PYTHONPATH:$(pwd) python lander/environment.py
```

## Visualize a trained agent

Once you have trained an agent you can see how it behaves. 

```shell
python enjoy.py logs/20220203-015918
```

# Training

This is the command used to launch a training:

```shell
python train.py -params n_steps:8192 max_grad_norm:0.2 ent_coef:0.0005 vf_coef:0.25 gamma:0.995 policy_kwargs:"dict(log_std_init=-2, ortho_init=False, activation_fn=torch.nn.ReLU, net_arch=[dict(pi=[128, 128], vf=[128, 128])])" learning_rate:0.000005 use_sde:1 sde_sample_freq:4 --steps 100000000 --output logs
```

# Contributing

- Coding style:
    ```shell
    pip install pre-commit
    pre-commit install
    ```
- Run tests:
    ```shell
    python -m unittest discover --pattern "*test.py"
    ```
