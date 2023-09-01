
# Embarking on Odyssey: Mastering Navigation Through Reinforcement Learning

## Overview

In this project, we delve into training an agent to effectively navigate through a vast, square environment while collecting yellow bananas. The main objective is to accumulate as many yellow bananas as possible while avoiding blue bananas. This endeavor involves employing deep reinforcement learning techniques to empower the agent's decision-making process.

![Random Agent](https://github.com/neelgandhi108/deep_reinforcement_learning_navigation/blob/master/results/random_agent.gif) | ![Trained Agent](https://github.com/neelgandhi108/deep_reinforcement_learning_navigation/blob/master/results/trained_agent.gif)

## Problem Statement

The environment bestows a reward of +1 upon collecting a yellow banana and a penalty of -1 for acquiring a blue banana. The agent's task is to learn to optimize its actions to maximize the cumulative rewards. The agent perceives the environment through a 37-dimensional state space, which includes its velocity and a ray-based view of objects in its forward direction. The agent can take one of four discrete actions:

-   **`0`** - move forward.
-   **`1`** - move backward.
-   **`2`** - turn left.
-   **`3`** - turn right.

The project is episodic, and the agent must achieve an average score of +13 over 100 consecutive episodes to solve the environment.

## Getting Started

To initiate this project, follow these steps:

1.  Download the environment suitable for your operating system using one of the links provided below:
    
    -   Linux: [download link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux.zip)
    -   Mac OSX: [download link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana.app.zip)
    -   Windows (32-bit): [download link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86.zip)
    -   Windows (64-bit): [download link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86_64.zip)
2.  After downloading, place the downloaded file in the same directory as this README file and unzip it. Then, specify the correct file path when creating the environment in the `Navigation_solution.ipynb` notebook:
    

pythonCopy code

`env = UnityEnvironment(file_name="Banana.app")` 

## Project Structure

The project comprises several important files:

-   `dqn_agent.py`: Contains the agent's code used in the environment.
-   `model.py`: Contains the Q-Network implementation used as the function approximator by the agent.
-   `dqn.pth`: Contains the saved model weights for the original DQN model.
-   `ddqn.pth`: Contains the saved model weights for the Double DQN model.
-   `dddqn.pth`: Contains the saved model weights for the Dueling Double DQN model.
-   `Navigation_exploration.ipynb`: Notebook for exploring the Unity environment.
-   `Navigation_solution.ipynb`: Notebook containing the solution.
-   `Navigation_Pixels.ipynb`: Notebook focusing on the pixel-action problem.

## Instructions

Follow the instructions provided in `Navigation_solution.ipynb` to begin training your agent. If you wish to observe a trained intelligent agent, adhere to the following instructions:

-   **DQN**: To run the original DQN algorithm, utilize the `dqn.pth` checkpoint to load the trained model. While defining the agent, set the `qnetwork` parameter to `QNetwork`, and the `update_type` parameter to `dqn`.
-   **Double DQN**: For executing the Double DQN algorithm, utilize the `ddqn.pth` checkpoint to load the trained model. While defining the agent, set the `qnetwork` parameter to `QNetwork`, and the `update_type` parameter to `double_dqn`.
-   **Dueling Double DQN**: To implement the Dueling Double DQN algorithm, use the `dddqn.pth` checkpoint to load the trained model. While defining the agent, set the `qnetwork` parameter to `DuelingQNetwork`, and the `update_type` parameter to `double_dqn`.

## Algorithm Enhancements

Several improvements have been incorporated into the original DQN algorithm:

-   **Double DQN**: Implementation based on the [paper](https://arxiv.org/abs/1509.06461) and [code](https://github.com/dalmia/udacity-deep-reinforcement-learning/blob/master/2%20-%20Value-based%20methods/Project-Navigation/dqn_agent.py#L94).
-   **Prioritized Experience Replay**: Work in progress.
-   **Dueling DQN**: Implementation based on the [paper](https://arxiv.org/abs/1511.06581) and [code](https://github.com/dalmia/udacity-deep-reinforcement-learning/blob/master/2%20-%20Value-based%20methods/Project-Navigation/model.py).

## Results

The plotted scores per episode provide insights into the learning progress. The environment was successfully solved in **377** episodes (currently).

Double DQN

DQN

Dueling DQN

![double-dqn-scores](https://github.com/neelgandhi108/deep_reinforcement_learning_navigation/blob/master/results/ddqn_new_scores.png)

![dqn-scores](https://github.com/neelgandhi108/deep_reinforcement_learning_navigation/blob/master/results/dqn_new_scores.png)

![dueling-double-dqn-scores](https://github.com/neelgandhi108/deep_reinforcement_learning_navigation/blob/master/results/dddqn_new_scores.png)

## Challenge: Learning from Pixels

The project initially involves the agent learning from its velocity and ray-based perceptions. For a more challenging task, learning directly from pixels is explored. A specialized Unity environment is provided for this purpose. This environment mirrors the project environment, with the crucial difference that the state now consists of an 84 x 84 RGB image, representing the agent's first-person view.

Please note that Udacity students should refrain from submitting a project using this new environment. Detailed instructions for using this setup are provided in the `Navigation_Pixels.ipynb` notebook.

## Dependencies

Install the required dependencies using the `requirements.txt` file located in the [main](https://github.com/neelgandhi108/deep_reinforcement_learning_navigation) folder:

bashCopy code

`pip install -r requirements.txt`