[image1]: ./score.png

Deep Determinisitc Policy Gradient Reinforcement Learning algorithm has been used to solve the Tennis environment. 





Details of learning algorithm are as follows:



1) An implementation of Deep Deterministic Policy Gradient has been created. Fully connected feedforward network as Actor is used as a function approximator to learn policy for agents and estimate
 action for given state. The neural network contains fully connected input, output and one hidden layer (called local actor network). A copy of the neural network is maintained (called target actor network) which provides target actions to learn for local network at every timestep.


2) Another fully connected feedforward network as Critic is used to estimate Q values of state-action pair. The action used to predict Q value is output of policy network (Actor) for the current state. A copy of the neural network is maintained (called target critic network) which provides Q value target to learn for local critic network at every timestep.



3) A memory buffer is used to save the experience tuple of agent (state,action,reward, next state).

4) Every few iterations target network is updated with a copy of the local network weights using soft update rule. A parameter tau is used  to decide the fraction of local network parameter copied on to target network parameters.


5) The agent uses random noise and adds it to the predict action values from the actor network to improve exploration.


6) Agent's experience tuple (state, action, reward, next state) is saved in the memory buffer.


7) local network is trained at every time step. A minibatch of experiences is sampled randomly at every time step from memory buffer and local network weights are updated using gradient descent. 


9) Each simulation is episodic. Envirnonment is considered solved when average score achieved by agent over last 100 iterations goes beyond a certain threshold.



10) The algorithm is set up such that both agents can be trained. All agents use the same actor-critic network and their experience tuples are saved in the same memory replay buffer.

11) Hyperparameters:

BATCH_SIZE = 128        # minibatch size
BUFFER_SIZE = int(1e5)  # replay buffer size
GAMMA = 0.99            # discount factor
LR_ACTOR = 1e-4         # learning rate of the actor 
LR_CRITIC = 1e-3        # learning rate of the critic
TAU = 1e-3              # for soft update of target parameters
WEIGHT_DECAY = 0        # L2 weight decay

12) Convergence plot:

![image1]

Future Outlook:


1) Experience samples from memory buffer are chosen at random. Selection criterion can be made based on the number of times an experience has already been chosen (by keeping a track of count). This should help neural network generalize over the state space.


2) The agent can keep a representation of explored area in some form. Action selection can be guided by such a representation so that exploration of the algorithm increases.
