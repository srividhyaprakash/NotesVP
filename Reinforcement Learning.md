

Reinforcement Learning Notes:

Terms:

Value of a state: (Value function) V(s)
    
    What is the total expected reward an agent can accumulate over the future, starting from this current state.

Policy: π
    
    The set of stochastic actions that one can take in that given state.
    It could be a mapping of all the states and corresponding actions possible in that state. 

Model: 
    
    Something that mimics the environment, (a simulation) and is able to tell us the next state and next reward given a particular action in a particular state.
    
Model-Free: 
    
    The agent is able to directly interact with the environment to solve the Reinforcement learning task.
    Advantage: The agent is able to obtain a accuracte model of the environment.
    Disadvantage: The agent may not be able to interact with the real-world environment as much as required due to cost factors and possible wear and tear in the case of robotics

Model-Based: 
    
    The agent is able to interact with a simulation of the environment.
    Advantage: The agent is able to perform different simulations thereby effectively exploring different states of the environment without causing any significant damage as this is a simulation.
    Disadvantage: The simulation of the environment might not depict a true picture of the real-world environment.  

Episodic:
    
    states come to a halt. i.e states terminate after a certain number of timesteps. For example, cluster tool once all the wafes have been processed.
    
Non-episodic (continuous): 
    
    states don't come to a halt. i.e states do not terminate. For example, robot learning to walk.
Off-policy: 
    
    The agent learns about the action-value function a = max Q(s,a,θ) while following the behaviour distribution thereby ensuring adequate exploration.
 
 
Behaviour Distribution ρ(s, a): 
    
    Probability distribution over states s and actions a. 

Evolutionary Algorithms:
    
    Multiple static policies are rolled out with each policy interacting with a separate instance of the enivronment. 
    The policies are made to interact with each other and the policies which generate the maximum reward are made to interact with in the next cycle. 
    
    This closely resembles biological evolution. Survival of the fittest kind. 

Monte-Carlo:
    
    Rewards are collected at the end of an episode and the next episode begins with the new knowledge.
    Update happens based on the following formula.
    
    V(St) = V(St) + alpha * (Gt - V(St))         --------> Vanilla Q-learning algorithm (Monte-carlo way)
    where 
        alpha = learning rate (LR is how quickly we want to forget the older estimated q value for this (s,a) pair. Lesser = forget slowly
        V(St) = Value function for state St, the current state
        Gt = Total Discounted reward
    
Temporal Difference (TD):
    
    Unlike Monte-Carlo methods, learning happens at each time step. This means that the value function at each state gets updated at that time-step. This is also TD(0).
    
    Update happens based on the following formula.
     
    V(St) = V(St) + alpha * (Rt+1 + gamma * V(St+1) - V(St))    --------> Vanilla Q-learning algorithm (TD way)
    where 
        alpha = learning rate (LR is how quickly we want to forget the older estimated q value for this (s,a) pair.  Lesser = forget slowly
        gamma = discount factor
        V(St+1) = Value function for state St+1, the next state
        V(St) = Value function for state St, the current state
        Gt = Total Discounted reward

Epsilon-Greedy Strategy:
    
    We set  1. a min-epsilon value. 0.1
            2. a max-epsilon value: 1.0
            3. decay rate: Typically set to 0.01
            4. Epsilon: Typically set to 1 in the beginning 
    Then we update epsilon at the end of each episode. Note: Update is done at the end of each episode. 
    epsilon = min_epsilon + (max_epsilon - min_epsilon)*np.exp(-decay_rate*episode)
    
    Theory:
        We want epsilon a.k.a exploration to be very high in the begining, as we dont know anything about the environment.
        Gradually decrease it to make the environment more exploitative. 

Value-based Methods:
    Deep Q Learning (DQN):
    
        Q Learning is primarily maintaining a 2-D matrix with the rows representing the states and the columns the actions. 
        The value at the cell of the 2-D matrix is how desirable it is to take that action in that particular state.
      
        Motivation for DQN-
            As you deal with more and more complex problems, your state space tends to grow exponentitally and maintaining a 2D matrix becomes inefficient and infeasible. 
            Instead, iteratively, we could come up with a function that tries to approximate the action value for each row and then, generalizing more, come up with a function that approximates the entire 2D matrix. Enter neural networks.
            
            In the past we have seen that Neural Networks have been notoriously good in approximation and trying to come up with functions for a given input and output. (Function approximators)
            
         Algorithm: 
            Deep Q networks are used for exactly, feed the inputs (pixels if you are playing a game or state of the environment as a list) and pass it through CNN or MLP respectively, and have the number of nodes in the output as the number of actions and a softmax layer at the output to give probabilites for each action and choose the action with the highest probability. 
         Update based on the following formula:
         
         
            Sample a mini-batch from the experience replay memory.
                
                Why we need the experience replay?
                    Say you are playing a game, games are sequential. Only if you complete first level, can you go the second level and so on,when you feed the first level and ask the NN to learn, it learns, when you do the second level, it learns, but it also forgets what it learnt in the first level. To break this high correlation that we feed to the NN, we sample random mini-batches from our stored experience buffer and ask the NN to learn from that.
            
            From the sampled mini-batch, see if that experience (state, action, reward, next_state, done) is a terminal state,
            meaning, done == True, if true then set the reward fo this experience to just reward or else use,
            
            reward + gamma * max(Qnext-state)
          This would be out target Q values, we calculate the loss based on the current Q values and update our parameters.
          

   Fixed Q-Networks:
         
         In the above case, we see that we are kind of chasing a moving reward, that is we are both updating the same Q networks weights and at the same time, trying the reach the same Q networks values, hence chasing a moving target.
         
         Solution, Simple: Don't move it for some time. Hence Fixed Q networks, i.e copy your target Q network to a separate memory. Try to reach that, and once in a while, copy your current Q network weights to that target Q network. 

   Double DQN's:
            
        Motivation:
        We are just naively thinking that the best action possible in the next-state is the one with the highest action value. What if that is wrong?
        
        Solution:
            It can be wrong and so use a DQN for that also. Hence double DQN.
            
   Duelling DQN:
    
        Just like the softmax layer, which gives us a probability of the best actions, (the probabilities sum upto 1) so it's kind of relative and we have a better perception about which action to take, we have the advantage function. The Advantage function is based on relative terms and it tells us how good it is to perform and what would be the difference in reward over other action.
        
        There is no change in updation algorithm, but now our CNN or MLP wil get split in the final layer, where one evaluates the value function of the state V(s) and another branch tells us the goodness of each action. We combine these two in the aggregation layer and finally have our result.
        
        
   Prioritized Experience Replay:
   
        In our experience buffer, it can so happen that some of the experiences are more important and hence need to be sampled regularly than the other ones. Previously we just sampled from the experience buffer uniformly. 
        This causes an issue. In updating. We need to update slowly as we are now sampling certain experiences more so than the others. If we update the experiences uniformly, we might run into the problem of over-fitting to the prioritiy sampled experiences.
        
Aside:
     
     1. Reinforcement Learning's (RL) major theoretical components are trial and error and optimal control. RL's trial and error should not be confused with Supervised Learning's trial and error where in supervised learning, we try to predict the final value through random initial weights and propagate back the error. This isnt trial and error. This is feedback. RL takes different actions for the same state (exploration) at different timesteps and evaluates the best action to take once converged.
     
     2. Value function approximators, one of the core of RL alogrithms, takes in a particular state s and returns the long-term reward r based on a set of parameters θ (w.r.t env)        Universal value function approximators are the first generalisation towards achieving human level performance in the sense that, they take in the goal as well, V(s, g, θ)
