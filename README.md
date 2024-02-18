# Reinforcement-Learning-Actor-Critic-Lunar-Lander
A reinforcement learning agent uses the actor-critic method to beat Atari's Lunar Lander. This implementation via a python notebook is set up to learn in 400 episodes with the agent exploring almost the entire time. This project was implemented per the requirements of the Reinforcement Learning Final Project rules. 

Environment:

Lunar Lander originally released by Atari in 1979 as a single-player arcade game.
The player attempts to land on the lunar surface by controlling main and side thrusters.
Our Lunar Lander environment is part of the Box2D environments [Box2D is a 2-dimensional physics engine for games (https://box2d.org/documentation/index.html)]
The observation space, or state, is an 8-dimensional vector which consists of:
2 floating point values representing the lander’s current position in (X, Y) coordinate space.
2 floating point values representing the lander’s linear velocity in (X, Y) coordinate space.
1 floating point value representing the lander’s current angle.
1 floating point value representing the lander’s angular velocity.
2 Boolean values representing whether each leg of the lander is in contact with the surface.

Action Space:

The action space consists of four discrete actions:
0: do nothing
1: fire left orientation engine
2: fire main engine
3: fire right orientation engine

Rewards:

Safe landing on lunar surface: 100
Crash landing on lunar surface: -100
Each leg in contact with surface (per leg): 10
Firing either side engine: -0.03
Firing main engine: -0.3

Reward Implications:

- reward increases as the lander nears the landing pad
- reward decreases when the lander is further away
- reward increases as the lander's velocity slows
- reward decreases as lander's velocity accelerates
- reward decreases as lander's angle tilts away from horizontal

Actor-Critic Method:

Actor – is responsible for selecting actions based on the current policy, where the policy defines a probability distribution for actions available in a given state.

Critic – evaluates actions taken by the Actor. It estimates the value of being in a particular state following current policy, with a goal of learning a value function for expected future rewards.

Neural Network Implementation:

![image](https://github.com/ashi-jne/Reinforcement-Learning-Actor-Critic-Lunar-Lander/assets/96357892/bb5eda4c-849f-400c-86fc-a3e97447f058)

Both networks have:
- 8 inputs of lander’s current state
- 2 fully connected hidden layers
- Rectified Linear Unit activation function for efficiency
- Implemented using PyTorch
Actor Network outputs the probability of 4 possible actions.
Critic Network outputs a score for actor’s action.
Both networks update after each step.

Learning Process:

- In the forward pass both networks take the state input, Actor returns the action policy and Critic returns an estimated value.
- Agent uses policy to select an action, observe rewards, and calculate expected cumulative rewards.
- Temporal difference (delta) = expected cumulative reward - estimated value
- Objective function is to minimize sum of the actor and critic losses.
- Backwards propagation using Adam Optimizer to update weights on the NNs.

Hypertuning parameters for learning:

![image](https://github.com/ashi-jne/Reinforcement-Learning-Actor-Critic-Lunar-Lander/assets/96357892/97300942-d628-4d57-9973-7aa60a3809bb)




