# FetchReach-v1

This project implements a Soft Actor-Critic (SAC) reinforcement learning agent using the **Tianshou** library to solve the **FetchReach-v1** environment from the **OpenAI Gym**. The code is built around efficient training and evaluation, including logging, saving agent models, and recording video episodes for performance analysis.

## Abstract

This project uses a Soft Actor-Critic (SAC) algorithm to train an agent to solve the FetchReach-v1 environment, which is a continuous control problem. The agent learns to reach a target position using a robotic arm in the MuJoCo simulator. The implementation leverages Tianshou's off-policy reinforcement learning framework, along with prioritized replay buffers to enhance learning efficiency. Key features include automated logging of metrics via TensorBoard, saving models at each epoch, and visualizing the agent's performance through recorded episodes.

## Key Features

- **Environment**: Utilizes the `FetchReach-v1` from OpenAI Gym, wrapped with `FilterObservation` and `FlattenObservation`.
- **Policy**: Soft Actor-Critic (SAC) policy implemented using Tianshou with support for exploration and entropy tuning.
- **Model Saving**: Saves the model and optimizer states periodically during training.
- **Buffer Type**: Uses a prioritized experience replay buffer with adjustable hyperparameters.
- **Logging**: Tracks training performance using Tensorboard, and video recordings of agent performance are saved periodically.
- **Neural Networks**: Actor and Critic networks have customizable hidden layers, with parameters optimized using Adam.

## Setup and Installation

1. Clone the repository and navigate to the project folder:
   ```bash
   git clone https://github.com/<your-repo>.git
   cd Tianshou_SAC_FetchReach
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Ensure that MuJoCo is installed and activated:
   ```bash
   sudo apt-get install mujoco
   ```

4. Run the training:
   ```bash
   python main.py
   ```

## Hyperparameters

The main hyperparameters used in the training are:

- **Hidden Layers**: Two layers of size 128.
- **Learning Rate**: `1e-3` for the actor and critic networks.
- **Prioritized Replay Buffer**: Alpha `0.7`, Beta `0.5`, and a buffer size of `1,000,000`.
- **Alpha Learning Rate**: `1e-4`.
- **Training Steps**: 100,000 steps per epoch.
- **Batch Size**: 64.
- **Seed**: 0 (for reproducibility).

## Training and Testing

The agent is trained using the off-policy SAC algorithm and a prioritized replay buffer. During the training process, the following steps are performed:

1. The agent interacts with the environment to collect experience, stored in the prioritized replay buffer.
2. After each epoch, the model and buffers are saved, and the agent’s performance is recorded.
3. Testing is performed by evaluating the agent on a test environment using the same policy.

The performance of the agent is periodically logged using Tensorboard and can be accessed by:
```bash
tensorboard --logdir './logs'
```

## Results

The final trained agent achieves a high success rate in reaching the target position in the FetchReach-v1 environment. The soft actor-critic algorithm's performance, combined with prioritized replay buffer, ensures stable and efficient learning.
