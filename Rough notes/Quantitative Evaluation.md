# 5-Step Approach to Design Controlled Experiments
## 1. Define the research question
### Start with a general question and change it to a specific one
- How does X compare to Y.
- => How does X compare to Y for what tasks in what context in term of what measures for which target population.
- Tasks: Need to decide what subset of tasks is appropriate to test.
- Performance = speed + accuracy + learnability: Need to be testable.
- Context: Need to decide what subset to test.
## 2. Determine variables 
- Independent variable (IV): Tasks & Factors manipulated in the experiment – Have multiple levels (ranges of values):
	- Primary
	- Secondary: Other interesting factors you want to manipulate in the experiment to answer the main question in a richer way.
- Dependent variable (DV): Factors measured
- Control variable are fixed factors during the experiment:
	- Confound: Factors that varied and was not accounted for: Order of test, Prior experience.
	- Problem: Confound could have caused change in DVs => difficult to draw conclusions
- Random variable: Randomly sampled factors => Increases generalizability
## 3. Arrange conditions
- IV => Experimental Conditions
- What is a condition?: Each unique combination of the different levels of the various IV's.
### Between-subject test
- 1 participant for each condition.
- Problems: Does not account well for individual differences => Expensive.
### Within-subject test
- 1 participant test all conditions.
- More economical.
- Problems: Does not account for the order effect as a confounding variable.
- Needs counter-balancing. Especially for primary variables!
### Control order effect using Counter-balancing
- If we assume the order effect is symmetric, which means A -> B = B->A, and is linear, which means the increment between different conditions is about the same, we can use counter-balancing to cancel the effect out:
	- Participant 1: A -> B.
	- Participant 2: B -> A.
- However, needs $N!$ participants!
### Partial Counter-balancing: Latin Square
- Ensures each level appears in every position in order equally often: 
	- A B C
	- B C A
	- C A B
- Steps:
	1. List all IV and their levels
	2. Decide counter-balancing strategy for each variable
	3. Determine the minimum No. of participants 
	4. Arrange the overall design
	5. Determine detailed arrangement for each participant
### However, Counter-balancing May not Always Work
- Counter-balancing Assumes symmetric transfer and linear increment
- If asymmetric transfer and non-linear increment:
	- Have to use Between-subjects design
	 - In addition, some factors have to be between-subject (Age, Gender, etc.)
### No. of Condition Reduction Strategies
- Pick the most important/interesting factors to test. 
- Run a few independent variables at a time 
	- If strong effect, include variable in future studies
	- Otherwise pick fixed control value for it
- Not all within-subject IVs need to be counter-balanced
## 4. Decide blocks and trials 
### Trial
- A single repetition of a single condition/cell
- Each trial in a condition is treated as equivalent with each other.
- At least 3 trials per condition.
- The number of trials is determined by the sample space.
### Block
- Indicates Learning
- An entire section of the experiment
- Repeated to analyze learning
![[User Study Blocks & Trials.png]]
### Determine Number of Blocks/Repetitions
- Must account for time, fatigue & enough data points for significant effects:
1. Estimate the time for each trial (At least 3 trials per condition) 
2. estimate the time for each block
3. balance the trials and blocks so that the main part of the experiment is within 45 minutes.
4. combine with the condition arrangement
## 5. Set instruction and procedures
1. Recruit participants (determine target users and randomize) 
2. Consent form and pre-experiment questionnaire 
3. Instructions:
	- Explain the goal, no hypotheses
	- Answer questions
1. Practice trials
2. Main experiment with breaks
3. Post-experiment questionnaire and interview
4. Debriefing
	- Inform users of the goal
	- Answer
### The Importance of Practice Trials
- Always, Always, Always Pilot Study First!!!!!
- The nicher the product, the more practice trials are needed
# Cross users comparison (Experiment)
- Once we got the results of users (perf., error, completion time, etc.) in different interface, 
- We compare which is better by considering mean + stdev + (null-hypothesis, t-test, ANOVA (more than 2 interfaces)).
- http://yatani.jp/teaching/doku.php?id=hcistats:start