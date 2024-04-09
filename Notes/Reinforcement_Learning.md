# Reinforcement Learning 🤖

Machine is agent that interacts with environment and receives rewards.

- Goal: Maximize rewards; No feedback in between, but only at the end

---

### 🖊 Info

Core-Metrics

- Average Reward should go up!
- Average Episode length should go up!

Training strategies:

- Train for longer
- Hyperparameter Tuning
- Try different algorithms

---

### Workflow

```txt

1) Load Environment
- Choose a gym or custom environment
- Define and understand the action + observation space
- Test the environment
- Wrap it in a Dummy-Environment

2) Train an RL-Model
- Choose a Policy-Strategy
- Let the Model learn

3) Save and Reload Model
- Choose a path

4) Evaluate Model
- Check Core-Metrics
- Average Reward should go up!
- Average Episode length should go up!
- Some algorithms have a "cap" –> Value that say it worked

5) Test Model
- ...

6) View Logs of Test
- Tensorboard
```

---

## 1) Environment

What are you trying to solve?

- [ ] **Environment** –> Where the Agent is operating
- [ ] **State s** –> Complete description of the state of the world
  - [ ] **State-Space** --> Set of all possible situations our agent could inhabit
  - [ ] **Observation** –> partial description of a state, may omit information
    - [ ] -> Fed to model to make predictions
    - [ ] **Fully / Partially Observed** -> When the agent can only see a partial observation
  - [ ] **Trajectory** -> Sequence of states and actions in the world
- [ ] OpenAI-Gym --> Several Game-Settings, Custom Environment

---

## 2) Agent

- [ ] **Agent** –> Operating in Environment, using an algorithm
  - [ ] **Action** --> What an agent does in the environment (per Step)
    - [ ] **Action-Space** --> Set of all possible actions our agent can take (discrete/continuous)
      - [ ] Discrete vs. Multi-Discrete vs. Continuous
    - [ ] **Step** --> Progress in Environment, take an action and return observation + reward

---

## 3) Model

What Algorithm are you using?

#### 🌵 2.1) Model-Free

##### Value-Based (Wertbasiert)

Agent determines utility function

- [ ] **Monte-Carlo-Methoden**
- [ ] [Temporal Difference Learning (TD)] --> Adjustment after each action, estimated reward
  - [ ] **Q-Learning** -->  The value of an action is evaluated, not the state.

##### Policy-Based (Strategie-Basiert)

Parametrisierung der Strategie, Gradientenbasiert

- [ ] **Proximal Policy Optimization (PPO)**--> Common approach
- [ ] **Trust Region Policy Optimization (TRPO)**
- [ ] **REINFORCE**
- [ ] **SARSA** --> Agent bleibt seiner Strategie treu (On-Policy)

---

#### 🌵 2.2) Model-Based

Prädikatives Modell, trifft Vorhersagen und plant

- [ ] **Dyna Algorithm**

---

## 4) Policy

- [ ] **Policy** -> rule used by an agent to decide what actions to take
  - [ ] **Deterministic (μ) Policies**
  - [ ] **Stochastic (π) Policies**
    - [ ] **Categorical policies** -> Discrete action spaces
    - [ ] **Diagonal Gaussian policies** -> Continuous action spaces
  - [ ] **Policy Parameters (θ)**
- [ ] [Off-Policy / On-Policy](https://towardsdatascience.com/on-policy-v-s-off-policy-learning-75089916bc2f)-> Festhalten an der Policy oder Entwicklung einer neuen, [Vergleichstabelle-Policy](image.jpg)

---

## 5) Reward / Penalty

- [ ] **Reward**
- [ ] **Return** -> Cumulative Reward
  - [ ] **Finite-horizon undiscounted return** -> sum of rewards obtained in a fixed window of steps
  - [ ] **Infinite-horizon discounted return** -> sum of all rewards *ever* obtained by the agent, but discounted by how far off in the future they’re obtained
- [ ] **Penalty**
- [ ] **Discount Factor**

#### Value-Function

- [ ] **Value Functions** -> expected return if you start in that state or state-action pair, and then act according to a particular policy forever after
  - [ ] **On-Policy Value Function**
  - [ ] **On-Policy Action-Value Function**
  - [ ] **Optimal Value Function**
  - [ ] **Optimal Action-Value Function**
- [ ] **Bellman backup** -> right-hand side of the Bellman equation
- [ ] **Advantage Function** -> How much is this particular action better than others?

---

## Variations / Phenomenons 🌀

- [ ] **Imitation Learning** --> Früheres Paradigma, Supervised Learning
  - [ ] [Behavioral Cloning](https://ml.berkeley.edu/blog/posts/bc/) –> Expert-Labelled Dataset, Force Agent to learn Behavior
    - [ ] **Goal-conditioned behavioral cloning** --> Explorativ, Wege zu versch. Zielen
- [ ] [Masking] –> Filter out unnecessary actions, restrict to set of useful actions
  - [ ] "Adding Domain-Knowledge into the Model"
- [ ] [Domain Randomization](https://developer.nvidia.com/blog/structured-domain-randomization-makes-deep-learning-more-accessible/) -> Learn in different versions of same environment
- [ ] [Exploration -/ Exploitation Tradeoff](https://towardsdatascience.com/the-exploration-exploitation-dilemma-f5622fbe1e82) --> Use well-known ('Exploit') or search new ('Explore')

#### Advanced Fields of RL

- [ ] Inverse Reinforcement Learning
- [ ] Transfer Learning, Meta-Learning
- [ ] Prediction (Model Based)

---

### 🧠 Notes

- Being greedy doesn't always work --> Optimise Rewards over long time
- Sequence matters in Reinforcement Learning --> Time is important
- Best gains come from:
  1.  Algorithm choice
  2.  Reward mechanism
  3.  Observation space
- Hyperparameter tweaking usually doesn't have such a great impact

---

### 💻 Webpages

- [ ] [Reinforcement Q-Learning from Scratch in Python with OpenAI Gym](https://www.learndatasci.com/tutorials/reinforcement-q-learning-scratch-python-openai-gym/)
- [ ] [Spinning up Reinforcement Learning (OpenAI)](https://spinningup.openai.com/en/latest/user/introduction.html)
- [ ] [TDM: From Model-Free to Model-Based Deep Reinforcement Learning](https://bair.berkeley.edu/blog/2018/04/26/tdm/)

---

- [ ] [Lecture series on Reinforcement Learning](https://www.youtube.com/watch?v=JHrlF10v2Og&list=PL_iWQOsE6TfURIIhCrlt-wj9ByIVpbfGc&index=1) --> Tip from Asma
- [ ] [Slides for the Lecture](https://rail.eecs.berkeley.edu/deeprlcourse/)

---
