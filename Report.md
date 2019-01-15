# Report
---
This project utilised the DDPG (Deep Deterministic Policy Gradient) architecture outlined in the [DDPG-Bipedal Udacity project repo](https://github.com/udacity/deep-reinforcement-learning/tree/master/ddpg-bipedal).

## State and Action Spaces
In this environment, a double-jointed arm can move to target locations. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of your agent is to maintain its position at the target location for as many time steps as possible.

The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector must be a number between -1 and 1.

## Learning Algorithm

For the  agent training  the `ddpg` function  (Deep Deterministic Policy Gradient)   will be used. 
We start in the  `Continuous_Control` notebook with the training over `n_episodes` or until the environment  is solved with average reward over the last 100 episodes  at least  equal  +30.0
Each episodehas  maximum  `max_t` time-steps .
The DDPG agent is contained in `ddpg_agent.py`

### DDPG Hyper Parameters
- n_episodes (int): maximum number of training episodes : 1000
- max_t (int): maximum number of timesteps per episode: 1000
- num_agents: number of agents in the environment : 1
- BUFFER_SIZE (int): replay buffer size :100000
- BATCH_SIZ (int): mini batch size  :128 
- GAMMA (float): discount factor  :  0.99   
- TAU (float): for soft update of target parameters  :1e-3   
- LR_ACTOR (float): learning rate for optimizer : 2e-4  
- LR_CRITIC (float): learning rate for optimizer : 2e-4  
- WEIGHT_DECAY (float): L2 weight decay : 0.0
- N_TIME_STEPS (int): every n time step do update : 3
,
### Neural Networks

Actor and Critic  models are defines in `ddpg_model.py`.

The Actor networks has  three fully connected layers with  relu activation and tanh activation for the action space. 
  - input: state size  output 256
  - input: 256  output 128
   - input: 128  output action size 

The Critic networks has  three fully connected layers with leaky_relu activation. 
  - input: state size  output 256
  - input: 256  output 128
   - input: 128  output 1
## Plot of rewards
Initialising ReplayBuffer
Episode 1	Score: 0.00	Average Score: 0.00.00
Episode 2	Score: 0.00	Average Score: 0.00.00
Episode 3	Score: 0.28	Average Score: 0.09.28
Episode 4	Score: 0.46	Average Score: 0.18.46
.....

Episode 349	Score: 27.28	Average Score: 29.9528
Episode 350	Score: 35.62	Average Score: 30.1062

Environment solved in 350 episodes!	Average Score: 30.10

 ![Reward Plot]( https://github.com/josef657/p2_con/blob/master/DDPG.png?raw=true)

## Ideas for Future Work
    -Fine tuning on the parameters can help us.

    -Parallel agent training.

    -I believe  that that Proximal Policy Optimization (PPO) and Distributed Distributional Deterministic Policy Gradients (D4PG) methods   can improve current results.  
