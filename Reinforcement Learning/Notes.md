Lecture 1: https://www.youtube.com/watch?v=8JVRbHAVCws <br>
Defintions: Agent: Something that can take an action by its own. E.g. In an autonomous drone, agent would be drone itself would be agent. Similarly for an ML algorithm the Algo itself is an Agent.<br>
Enviornment: Place where agent takes action and operates is called as enviornment<br>
Actions (a(t)): All possible moves that an agent can perform in the given enviornment is called as actions. E.g. In the 2D space an agent can move right, left up or down and these represents all the action that agent can take.<br>
Observations: How enviornment interacts back with the agent after the actions are performed.<br>
Single State(s(t+1)): The immediate situation in which agent finds itself is defined as single state. <br>
Reward: Feedback of an action performed which is either a sucess or failure. It can be immediate e.g. While playing Mario once you touch the gold coin the points immediately incerases or it can be delayed as well e.g.
Picking up right set of stocks today will result in profits when markets go up. <br>
Reward Return = $⨊ri(i=1->inf)$<br>.
It represents the sum of reward at all times <br>
Discounted Returns = $⨊Ɣ(i)*ri(i=1->inf)$<br>
Here discounting is important for the reason that it will make future rewards much less compared to present reward<br>
A reward of $5 today would be more than $5 offered tomorrow or later in time <br>
Total Reward (rep. by Rt) i.e. Rt = rt + Ɣ^1r(t+1) + Ɣ^2r(t+2)+ ....... <br>
Defining a Q-function <br>
Def: Q function takes two inputs i.e. state st  and action at and essentially return the total future reward considering you you take the action <br>
Q-(st,at) = E[Rt|st, at] <br>
Question: Now once that we know what is the Q function, what action should one take ? <br>
Answer: The actions should be the one that maximies the reward function <br>
### Training a Deep Q Network 
There are two possible ways to train a deep Q network
1. Train a network at all possible states and for a given action t which would result in Qt(S,a)
2. Train a network for all possible actions given state t which would result in Qt(S,a1),Qt(S,a2) etc and the final output can be  Pi(s) = argmaxQ(s,a)

**Policy Function** <br>
Policy function takes state st as input and returns the probabilistic distribution of all possible action. The ultimate goal is to find a optimal policy function that would try to optimize agent's long term reward







