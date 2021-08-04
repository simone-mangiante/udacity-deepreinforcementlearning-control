# udacity-deepreinforcementlearning-navigation

In this project I train a DDPG agent to solve the [Reacher](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#reacher) environment.

![reacher](reacher.gif "Reacher environment")

## Environment

In this environment, a double-jointed arm can move to target locations. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of your agent is to maintain its position at the target location for as many time steps as possible.

The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints.
Every entry in the action vector should be a number between -1 and 1.

There are two versions of this environment:
- the first version contains a single agent
- the second version contains 20 identical agents, each with its own copy of the environment

The second version is useful for algorithms like PPO, A3C, and D4PG that use multiple (non-interacting, parallel) copies of the same agent to distribute the task of gathering experience.

I focused on solving this second version.
To solve it, trained agents must get an average score of +30 (over 100 consecutive episodes, and over all agents). Specifically:
- after each episode, the rewards that each agent received (without discounting) are added up to get a score for each agent. This yields 20 (potentially different) scores and I take the average of these 20 scores
- this yields an average score for each episode (where the average is over all 20 agents).

So the environment is considered solved when the average (over 100 consecutive episodes) of those average scores is at least +30.

## Setup

### Step 1: Activate the environment
If not done already, please follow the [instructions in the DRLND GitHub repository](https://github.com/udacity/deep-reinforcement-learning#dependencies) to set up your Python environment. These instructions can be found in `README.md` at the root of the repository. By following these instructions, you will install PyTorch, the ML-Agents toolkit, and a few more Python packages required to complete the project.

(For Windows users) The ML-Agents toolkit supports Windows 10. While it might be possible to run the ML-Agents toolkit using other versions of Windows, it has not been tested on other versions. Furthermore, the ML-Agents toolkit has not been tested on a Windows VM such as Bootcamp or Parallels.

### Step 2: Download the Unity Environment
There is no need to install Unity, you can download a pre-built environment from one of the links below. You need only select the environment that matches your operating system:

#### Version 1: One (1) Agent
- Linux: click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Linux.zip)
- Mac OSX: click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher.app.zip)
- Windows (32-bit): click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86.zip)
- Windows (64-bit): click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86_64.zip)

#### Version 2: Twenty (20) Agents
- Linux: click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux.zip)
- Mac OSX: click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher.app.zip)
- Windows (32-bit): click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86.zip)
- Windows (64-bit): click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86_64.zip)

Then, place the file in the `p2_continuous-control/` folder in the DRLND GitHub repository, and unzip (or decompress) the file.

(For Windows users) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

(For AWS) If you'd like to train the agent on AWS (and have not enabled a [virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux_NoVis.zip) to obtain the "headless" version of the environment. You will not be able to watch the agent without enabling a virtual screen, but you will be able to train the agent. (To watch the agent, you should follow the instructions to enable a virtual screen, and then download the environment for the Linux operating system above.)

### Step 3: Explore the Environment
After you have followed the instructions above, open `Continuous_Control.ipynb` (located in the `p2_continuous-control/` in the DRLND GitHub repository) and follow the instructions to learn how to use the Python API to control the agent.

## Implementation code
My code is distributed in these files:
- [model.py](model.py) which contains the definition of the DDPG actor and critic networks
- [ddpg_agent_new.py](ddpg_agent_new.py) which contains the definition of the agent and the experience replay buffer
- [Continuous_Control.ipynb](Continuous_Control.ipynb) which is the main Jupyter notebook to train and watch an agent

## Results
Results of my experiments are documented [here](Report.md)