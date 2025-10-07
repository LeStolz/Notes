# Naturalistic approach
- Observation occurs in realistic setting
- Problems:
	- Hard to arrange and do
	- Time consuming
	- May not generalize
# Usability engineering
- Is the test result relevant to the usability of real products in real use outside of lab?
- Problems:
	- Non-typical users
	- Non-typical tasks
	- Different physical environment
	- Different social context
- Partial Solution:
	- Use real users
	- Task-centered system design tasks
	- Environment similar to real situation
# Discount usability evaluation
- Low cost methods to gather usability problems
- Qualitative:
	- Observe interactions 
	- Gather explanations
	- Produces description
	- Anecdotes, transcripts, problem areas, critical incidents…
- Quantitative:
	- Count, log, measure user actions
	- Speed, error rate, counts of activities
- Must turn qualitative (words) into quantitative (numbers).
- Methods:
	- Inspection
	- Extracting the conceptual model
	- Direct observation:
		- think-aloud
		- constructive interaction
		- Retrospective Think Aloud
	- Query techniques (interviews and questionnaires)
	- Continuous evaluation (user feedback and field studies)
## Inspection
- Designer tries it: Does it “feel right”?
- Benefits: Catch major problems early
- Problems: not reliable, not valid, intuition can be wrong.
- Methods:
	- Task centered walkthroughs
	- Heuristic evaluation
### Usability Heuristic Evaluation
- “Rules of thumb” describing features of usable systems
- Pros:
	- Easy and inexpensive
	- No need users
	- Catch many design flaws
- Cons: 
	- Not a simple checklist
	- Cannot assess how well the interface will address user goals
- H1-1: Simple and natural dialog
- H1-2: Speak the users’ language
- H1-3: Minimize users’ memory load
- H1-5: Feedback
- H1-6: Clearly marked exits:
	- Cancel button or Esc
	- Undo
- H1-7: Shortcuts
- H1-8: Precise & constructive error messages
- H1-10: Help and documentation
	- Easy to search
	- Focused on the user’s task
	- List concrete steps to carry out but not too long
- H2-1: Visibility of system status
- H2-2: Match system and real world
- H2-3: User control and freedom
- H2-4: Consistency and standards
- H2-5: Error prevention
	- Don't allow typing of invalid input + Describe input clearly
- H2-6: Recognition rather than recall
- H2-7: Flexibility and efficiency of use
	- Accelerators, Mneumonics, macros
- H2-8: Aesthetic and minimalist design
	- No irrelevant information in dialogues
- H2-9: Help users recognize, diagnose and recover from errors
	- ![[Pasted image 20240418063720.png]]
#### The Process of Heuristic Evaluation
##### Pre-evaluation training
##### Evaluation
- Individuals evaluate interface based on violations of heuristics then aggregate results
- Work in 2 passes (Go through UI twice): Overview -> Details
- Each evaluator produces own list of problems
##### Severity rating
- 0 << 1 << 2 << 3 << 4
- Not a problem << Cosmetic << minor << major << catastrophic
- Combination of Frequency, Impact, Persistence (one time or repeating).
- Should be calculated after all evaluations are in
- Should be done independently by all judges
##### Debriefing
- Discuss outcome, characteristics with evaluators, observers, and team members
- Suggest solutions
- Assess difficulty to fix
- A brainstorming session => Little criticism until end of session
#### Number of Evaluators
- Depends on market for product: popular products => high support cost for small bugs
- 3 - 5 evaluators find ~ 75% of usability problems
- Make sure it is cheaper than user testing
## Conceptual model extraction
- Show users static images of the prototype and ask them to explain the function of each element, how they would perform a particular task.
- Needs: Initial conceptual model (first time) & Formative conceptual model (later)
- Good for eliciting people’s understanding before & after use
- Poor for examining system exploration and learning 
## Direct observations
- Observes users interacting with system:
	- in lab: user asked to complete a set of pre-determined tasks
	- in field: user goes through normal duties
- Excellent at identifying gross design/interface problems
- Validity depends on how controlled/contrived the situation is
### Simple observation method
- User is given the task and evaluator just watches the user
- Does not give insight into the user’s decision process or attitude
### Think aloud method
- Users speak their thoughts while doing the task
- Gives insight into what the user is thinking
- Unnatural (awkward and uncomfortable), hard to talk if they are concentrating, may alter the way users do the task
### Constructive interaction method
- Solves unnatural part of think-aloud.
- Two people work together on a task, evaluator monitors their conversations.
- Co-discovery learning:
	- Use semi-knowledgeable “coach” and novice.
	- Only novice uses the interface
	- Novice ask questions, coach responds
- Gives insights into two user groups
### RTA – Retrospective Think Aloud
- Solves concentration part of think-aloud
- Process is observed and recorded with notes
- Benefits: Verbalizing on a higher level, More relaxed, Fabrication not a problem 
- Comparing Eye-tracking Patterns
# Steps to Prepare and Conduct a User Study
## Preparing
- Objective: narrow or broad?
- Design the tasks: 
	- Clear, specific (thus measurable), goal orientated
	- Representative and close to realistic (Focus on potential problems of the design)
	- How will you handle interventions?
- Decide on whether to use video/audio
- Choose the setting
- Representative users
## User Test roles
- Greeter
- Facilitator: Help users to think aloud…
- Observers: Record “critical incidents”:
	- Unusual or interesting events.
	- Most are usability problems.
	- When the user get stuck or suddenly understood something ("that's cool",...)
## User Test
- Greet the user:
	- Introduce yourself: Give background
	- "You're helping us by trying out this product in its early stages."
	- "If you have trouble, it's the product's fault, not yours. 
	  Don't feel bad; that's exactly what we're looking for."
	- "Although I don't know of any reason for this to happen, 
	  if you should become uncomfortable or find this test objectionable in any way, you are free to quit at any time."
- Collect Demographic Information:
	- Age, Gender, Occupation
	- Related questions
- Get user’s signed consent
- Explain the test
	- Talk about the equipment in the room and how it is used in the test.
	- "We have found that we get a great deal of information from these tests if we ask people to think aloud. Would you like me to demonstrate?"
	- Explain that you cannot provide help.
- Demo the system:
	- Demo the system
	- Describe the tasks in order. Give written instructions if needed
	- introduce the product.
	- "Are there any questions?"
- Run the test (maybe ½ hour):
	- "master-apprentice": Observe, take notes, but help the user describe what they’re doing
	- Keep the user at ease.
	- Make sure the equipments work
	- Make clear when the users move from a task to another
- Post-Interview & Questionnaire
	- System usability scale. Sum of scores of all questions * 2.5. 68 is average.
	- NASA task load index: https://humansystems.arc.nasa.gov/groups/TLX/downloads/TLXScale.pdf rates perceived workload in order to assess performance
	- [User Interface Usability Evaluation with Web-Based Questionnaires (garyperlman.com)](https://garyperlman.com/quest/)
	- Your own.
- Debrief:
	- Explain what you were trying to find.
	- Answer any remaining questions.
	- Discuss any interesting behaviors you would like the participant to explain.
## Use the results
- Update task analysis and rethink design:
	- Rate severity & ease of fixing problems
	- Fix both severe problems & make the easy fixes
- Will thinking aloud give the right answers?
	- Not always
	- If you ask a question, people will always give an answer, even it is has nothing to do with the facts 
	- Try to avoid leading questions
## How many users should you observe?
- best user 10x faster than slowest
- best 25% of users ~2x faster than slowest 25%
- Partial solution
	- Reasonable number of users with reasonable range
	- Big problems usually detected with 3-5 users
	- Small problems / fine measures need many users