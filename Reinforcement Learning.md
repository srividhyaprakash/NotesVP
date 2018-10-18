# Gym-Tensorforce-Learn
Learning OpenAI Gym and Tensorforce library

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
    
Non-episodic: 
    
    states don't come to a halt. i.e states do not terminate. For example, robot learning to walk.si
Off-policy: 
    
    The agent learns about the action-value function a = max Q(s,a,θ) while following the behaviour distribution thereby ensuring adequate exploration.
 
 
Behaviour Distribution ρ(s, a): 
    
    Probability distribution over states s and actions a. 

Evolutionary Algorithms:
    
    Multiple static policies are rolled out with each policy interacting with a separate instance of the enivronment. 
    The policies are made to interact with each other and the policies which generate the maximum reward are made to interact with in the next cycle. 
    
    This closely resembles biological evolution. Survival of the fittest kind. 


Aside:
     
     1. Reinforcement Learning's (RL) major theoretical components are trial and error and optimal control. RL's trial and error should not be confused with Supervised Learning's trial and error where in supervised learning, we try to predict the final value through random initial weights and propagate back the error. This isnt trial and error. This is feedback. RL takes different actions for the same state (exploration) at different timesteps and evaluates the best action to take once converged.
     
     2. Value function approximators, one of the core of RL alogrithms, takes in a particular state s and returns the long-term reward r based on a set of parameters θ (w.r.t env)        Universal value function approximators are the first generalisation towards achieving human level performance in the sense that, they take in the goal as well, V(s, g, θ)
