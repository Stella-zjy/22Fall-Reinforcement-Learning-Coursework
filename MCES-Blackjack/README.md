# Monte Carlo ES (Exploring Starts) Algorithm for Blackjack

======================================================================================================
Description:
This program uses MCES Algorithm to solve the Blackjack problem.
Specifically, several restrictions are made.
1. Ace only counted as 11 (not 1, not usable).
2. The dealer only hits when dealer's sum is less than or equal to 16.
3. Goal of the game is to get as close as possible to (but not exceed) 22.
4. Use an infinite deck of cards, with each face card (ace, two, three,.., ten, jack, queen, king) 
    having 1/13 probability of being drawn.
5. The player will always hit until it gets to at least 12. 
    The episode only starts when the player is at 12 or higher.
6. The first action (once at 12 or higher) will be randomly chosen between hit and stick, 
    then the current policy is to be followed.

======================================================================================================
Execution:
To execute the program, simply run the Jupyter Notebook in this directory.
No compilation is needed.

======================================================================================================
Program Overview:
Below are the functions implemented in my program.
<!-- First, I present all the utility functions. -->

1. initialization(S, A): returns Pi, Q, Returns as empty dictionaries

2. hit(): returns a random card value, which means the value in our setting is (11, 2, 3, ..., 10)    where 10 has probability 4/13 and others with probability 1/13

3.  generate_episode(S0, A0, Pi): returns an episode as a list from S0, A0, following Pi

4. evaluation(S, Pi, NUM_EPISODES): evaluates the current policy Pi by running NUM_EPISODES episodes  and returns the average return

5. display_policy(Pi): plots the policy according to states as a colorbar

<!-- So far I've covered all the utility functions covered in my program.
Now I'll cover the main loop functions for MCES algorithms. -->

6.  MCES_main(S, A, NUM_LOOP, EVAL_EVERY_NUM, NUM_EVAL_EPISODES): This is the main loop for MCES for estimating optimal policy. We train for NUM_LOOP times and every EVAL_EVERY_NUM training epochs and evaluate the returns over NUM_EVAL_EPISODES number of episodes.

<!-- Below are the two functions for experiments (under different experiment settings).
Both of them give a return history during the training and plot the optimal policy. -->

7. main_original_version(S, A): After training n???1000 steps, run 100 episodes with the current policy (no random initial action) and calculate the average return for those 100 episodes. Provide the average returns for n = 1, 2, ..., 20.

8. main_new_version(S, A): Train for 100,000 steps (instead of 20,000 steps). Every 1000 steps, evaluate the current policy by running 1000 episodes and averaging over the 1000 episodes.
