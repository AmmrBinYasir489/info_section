# Artificial Intelligence – Complete Exam-Oriented Notes

> **Based strictly on your uploaded PDFs (Chapter 5, 6, 7) + standard AI syllabus**
> Language: Simple, clear, exam-focused (definition → explanation → example → keywords)

---

## 1. MINIMAX ALGORITHM

### Definition

Minimax is a **decision-making algorithm** used in **two-player, turn-based, zero-sum games** (e.g., Chess, Tic-Tac-Toe). One player tries to **maximize** the score (MAX), while the other tries to **minimize** it (MIN).

### Key Assumptions

* Players play optimally
* One MAX player, one MIN player
* Game is deterministic
* Complete information game

### Game Tree

* Nodes = game states
* Edges = moves
* Leaf nodes = terminal states (win/lose/draw)
* Values assigned at leaf nodes

### Working (Step-by-Step)

1. MAX starts the game
2. MIN plays next
3. Values propagate **from leaf to root**
4. MAX chooses maximum value
5. MIN chooses minimum value

### Mathematical View

* MAX node → max(children)
* MIN node → min(children)

### Example

```
        MAX
      /      \
    MIN      MIN
   /   \    /   \
  3     5  2     9
```

* MIN chooses (3, 2)
* MAX chooses max(3,2) = **3**

### Time Complexity

* **O(b^d)**

  * b = branching factor
  * d = depth

### Space Complexity

* **O(bd)**

### Exam Keywords

* Adversarial search
* Game tree
* MAX/MIN players
* Optimal decision

---

## 2. ALPHA-BETA PRUNING

### Definition

Alpha-Beta pruning is an **optimization technique** for Minimax that **eliminates unnecessary branches** from the game tree without affecting the final result.

### Alpha (α)

* Best value MAX can guarantee so far

### Beta (β)

* Best value MIN can guarantee so far

### Pruning Condition

* If **β ≤ α**, stop exploring that branch (prune)

### Why Pruning Works?

Because a rational opponent will never allow a worse outcome.

### Example Idea

* MAX already has a move with value 5
* MIN finds a branch with value ≤ 3
* No need to explore further

### Advantages

* Faster than Minimax
* Same optimal decision

### Time Complexity

* Best case: **O(b^(d/2))**
* Worst case: **O(b^d)** (same as Minimax)

### Exam Keywords

* Pruning
* Alpha cut-off
* Beta cut-off
* Optimization of Minimax

---

## 3. CONSTRAINT SATISFACTION PROBLEM (CSP)

### Definition (From PDF – VERY IMPORTANT)

A CSP consists of:

1. **Variables**: {X1, X2, … Xn}
2. **Domains**: Di ≠ Ø
3. **Constraints**: {C1, C2, … Cn}

### CSP State

Assignment of values to **some or all variables**

### Legal / Consistent Assignment

Assignment that **does not violate constraints**

### CSP Solution

A **complete assignment** satisfying all constraints

### Example: Map Coloring

* Variables: WA, NT, SA
* Domain: {Red, Green, Blue}
* Constraint: Adjacent regions ≠ same color

### CSP as Search Problem

* Initial State: Empty assignment
* Successor: Assign value without conflict
* Goal Test: Complete assignment

### Types of CSPs (From PDF)

* Finite Domain (8-Queens)
* Boolean CSP
* Infinite Domain CSP
* Unary, Binary CSP
* Linear & Non-linear constraints

---

## 4. BACKTRACKING SEARCH (CSP)

### Definition

Depth-First Search based approach for CSP

### Steps

1. Assign variable
2. Check constraints
3. If fail → backtrack

### Heuristics (VERY IMPORTANT)

#### MRV (Minimum Remaining Values)

* Choose variable with **least legal values**
* Fail-first heuristic

#### Degree Heuristic

* Choose variable with **most constraints**

#### Least Constraining Value

* Choose value that **eliminates fewest options** for neighbors

---

## 5. FORWARD CHECKING & ARC CONSISTENCY

### Forward Checking

* Remove illegal values from neighboring domains

### Limitation

* Does not check neighbor-to-neighbor conflicts

### Arc Consistency

* Every value in Xi must have a **supporting value** in Xj

### AC-3 Algorithm

* Uses queue
* Re-check arcs after deletion

### Exam Keyword

* Constraint propagation

---

## 6. KNOWLEDGE-BASED (KB) AGENTS

### Definition

Agents that **store knowledge**, **reason**, and **infer new facts**

### Core Components

* Knowledge Base (KB)
* TELL → add knowledge
* ASK → query knowledge

### Why KB Agents?

* Flexibility
* Can work in partially observable environments
* Can learn new facts

### General KB Agent Cycle

1. Perceive
2. TELL KB
3. ASK KB
4. Act

---

## 7. WUMPUS WORLD (FROM PDF)

### Environment

* 4×4 grid
* Pits, Wumpus, Gold

### Sensors

* Breeze → Pit nearby
* Stench → Wumpus nearby
* Glitter → Gold

### Performance

* +1000 gold
* -1000 death

### Importance

Used to explain **logical inference**

---

## 8. LOGIC FUNDAMENTALS (EXAM FAVORITE)

### Syntax

Structure of sentences

### Semantics

Meaning of sentences

### Model

Assignment where sentence is true

### Entailment (⊨)

If KB ⊨ α, then α is true in **all models of KB**

### Tautology

Always true → P ∨ ¬P

### Contradiction

Always false → P ∧ ¬P

---

## 9. FIRST ORDER LOGIC (FOL)

### Why FOL?

Propositional logic only handles facts
FOL handles:

* Objects
* Relations
* Functions

### Components

* Constants: John, Richard
* Predicates: King(x)
* Functions: FatherOf(x)

### Atomic Sentence

Predicate(Terms)
Example: King(John)

### Quantifiers

#### Universal (∀)

"For all"
∀x King(x) → Person(x)

#### Existential (∃)

"There exists"
∃x Pit(x)

---

## 10. REINFORCEMENT LEARNING (INTRO – BASIC)

### Definition

Learning by **interaction with environment** using rewards

### Components

* Agent
* Environment
* Reward
* Policy

### Goal

Maximize cumulative reward

---

## 11. MINIMUM EDIT DISTANCE (MED) — *NLP Topic, Exam-Focused*

### What is Minimum Edit Distance?

Minimum Edit Distance (MED) measures **how different two strings are** by counting the **minimum number of operations** required to convert one string into another.

👉 **Lower distance = more similar strings**

This standard version is called **Levenshtein Distance**.

---

### Allowed Operations (Cost = 1)

1. **Insertion** – add a character
2. **Deletion** – remove a character
3. **Substitution** – replace one character with another

📌 If characters are the same → substitution cost = **0**

---

### Core Idea (One Line)

"Convert string A into string B using the fewest edits."

---

### Why Dynamic Programming is Used?

* Problem has **overlapping subproblems**
* Optimal solution depends on previous solutions
* We solve it using a **matrix (table)**

---

### Step-by-Step MED Algorithm

#### Step 1: Create the Matrix

If:

* Source string length = m
* Target string length = n

Create a matrix of size **(m+1) × (n+1)**

Rows → source word
Columns → target word

---

#### Step 2: Initialize the Matrix

**First Row:**
0, 1, 2, 3, … n  → only insertions

**First Column:**
0, 1, 2, 3, … m → only deletions

📌 This represents conversion to/from an **empty string** and is **mandatory in exams**.

---

#### Step 3: Fill the Matrix (Main Formula)

For each cell (i, j):

1. Compare characters

   * Same → substitution cost = 0
   * Different → substitution cost = 1

2. Apply formula:

cell(i,j) = min(

* Deletion → top cell + 1,
* Insertion → left cell + 1,
* Substitution → diagonal cell + cost
  )

---

#### Step 4: Final Answer

The **bottom-right cell** contains the **Minimum Edit Distance**.

---

### Simple Example

Convert:
**cat → cut**

Only one substitution needed:

* a → u

✅ Minimum Edit Distance = **1**

---

### Full Exam Example (Very Important)

Convert:
**intention → execution**

Matrix Details:

* Rows = prefixes of *intention*
* Columns = prefixes of *execution*
* # represents empty string

Each cell stores minimum edit distance between prefixes.

---

### Why Some Values Decrease in Matrix?

When characters **match**:

* substitution cost = 0
* diagonal value reused

Examples:

* i matches i
* o matches o
* n matches n

This reduces total cost.

---

### Final Result

Bottom-right cell = **8**

📌 Minimum Edit Distance(intention, execution) = **8**

Meaning:
8 edit operations are required to convert *intention* into *execution*.

---

### Importance of MED in NLP

* Spell checking (teh → the)
* Autocorrect systems
* Search engines
* Text similarity
* Sequence alignment

---

### How to Write MED in an Exam (Golden Steps)

1. Define Minimum Edit Distance
2. Draw and label the matrix
3. Show initialization
4. Write recurrence relation
5. Explain character matching
6. Circle bottom-right value
7. State final distance in words

---

### One-Line Summary (MCQ Ready)

Minimum Edit Distance computes the smallest number of insertions, deletions, and substitutions needed to transform one string into another using dynamic programming.

---

## LAST-MINUTE EXAM TIPS

* Write definitions first
* Use diagrams where possible
* Mention keywords (MAX, MIN, KB, Model, Entailment)
* For CSP → always write **Variables, Domains, Constraints**

---

✅ **This document covers EVERY minor detail from your PDFs**

When you upload **Intro to RL / NLP PDFs**, I will extend this same document.

---

## 🔹 Chapter 10: Introduction to Reinforcement Learning (RL) — *Fully from PDF*

### What is Reinforcement Learning (RL)?

Reinforcement Learning is a type of machine learning where **learning occurs through interaction with the environment**, not from a fixed dataset or explicit teacher. The agent learns by **trial and error**, observing the consequences of its actions in the form of rewards or penalties. fileciteturn1file0

Key ideas from PDF:

* Learning through interaction
* No explicit instruction about correct actions
* Focus on cause–effect relationship
* Goal is to maximize cumulative reward

**Formal Definition:**
RL is about learning how to map **situations (states)** to **actions** so as to **maximize a numerical reward signal** over time. fileciteturn1file0

---

### Intro to RL (Core Characteristics)

* Learner is **not told which action to take**
* Best actions are discovered through experimentation
* Actions affect both **immediate reward** and **future states**
* Learning is based on **trial-and-error search**
* Rewards may be **delayed** fileciteturn1file0

---

### Markov Decision Process (MDP)

RL problems are commonly modeled using **Markov Decision Processes (MDPs)**.

Assumptions about the agent:

* Can sense the environment (state)
* Can take actions that affect the state
* Has goals related to the environment

MDP includes:

* States
* Actions
* Rewards
* State transitions fileciteturn1file0

---

### Exploration vs Exploitation Trade-off

A fundamental challenge in RL:

**Exploitation:**

* Choosing actions that gave high rewards in the past

**Exploration:**

* Trying new actions to discover better strategies

Important Points:

* Only exploitation → may miss better solutions
* Only exploration → no learning stability
* Balance is necessary
* This trade-off **does not exist in supervised learning** fileciteturn1file0

---

### Examples of Reinforcement Learning

From PDF:

* Chess player choosing moves by planning + intuition
* Adaptive control in petroleum refinery
* Gazelle learning to run shortly after birth
* Mobile robot deciding when to recharge battery fileciteturn1file0

Common Features:

* Agent interacts with environment
* Decisions affect future states
* Long-term consequences matter
* Environment is uncertain

---

### Elements of Reinforcement Learning

Four main components:

1. **Policy (π)**
2. **Reward Function (R)**
3. **Value Function (V)**
4. **Model of Environment (optional)** fileciteturn1file0

---

### Policy

* Defines agent behavior
* Maps states → actions
* Core component of RL agent
* Can be:

  * Simple (lookup table)
  * Complex (search / computation)
  * Stochastic (probabilistic actions) fileciteturn1file0

---

### Reward Function

* Defines the goal
* Maps states or state-action pairs → numerical reward
* Agent aims to maximize long-term reward
* Analogy: pleasure & pain
* Reward is **given by environment** and **cannot be changed by agent**
* Can be stochastic fileciteturn1file0

---

### Value Function

* Measures long-term goodness of a state
* Value = expected total reward from that state onward

Difference:

* Reward → immediate
* Value → long-term

Important:

* High reward state may have low value
* Low reward state may have high value

Values are predictions of rewards and are harder to estimate fileciteturn1file0

---

### Relationship Between Reward & Value

* Rewards are primary
* Values are secondary (predictions)
* Decisions are made using **values**, not immediate rewards
* Most RL algorithms focus on value estimation fileciteturn1file0

---

### Models in Reinforcement Learning

**Model of Environment:**

* Predicts next state and reward
* Used for planning

Evolution:

* Early RL: trial-and-error only
* Modern RL: combines learning + planning
* Related to dynamic programming and state-space planning fileciteturn1file0

---

### Extended Example: Tic-Tac-Toe (Very Important for Exam)

**Problem Setup:**

* Play against imperfect opponent
* Draw = loss
* Goal: exploit opponent mistakes

**Why Minimax Fails:**

* Assumes optimal opponent
* Cannot exploit poor moves

**Why Dynamic Programming Fails:**

* Requires full opponent model
* Unrealistic

---

### RL Solution for Tic-Tac-Toe

**Value Function Approximation:**

* Maintain table of state values
* Win → 1
* Loss / Draw → 0
* Other states → 0.5 initially

**Learning Strategy:**

* Greedy moves (best value)
* Exploratory moves (random)

**Update Rule (Temporal Difference):**
V(s) ← V(s) + α ( V(s′) − V(s) )

Ensures convergence to optimal policy fileciteturn1file0

---

### Evolutionary vs Value Function Methods

**Evolutionary Methods:**

* Evaluate complete policies
* Credit given to all actions
* Uses hill climbing, genetic algorithms

**Value Function Methods:**

* Evaluate individual states
* Learn incrementally
* More precise and adaptive fileciteturn1file0

---

### Key Characteristics of RL

* Learns from interaction
* Adapts to opponent/environment
* No explicit planning required
* Can handle large state spaces
* Can use prior knowledge
* Suitable for episodic & continuous tasks fileciteturn1file0

---

### Real-World Application

* Backgammon (Tesauro, 1992–95)
* Used neural networks + RL
* Achieved world-class performance
* Handled ~10²⁰ states

---

## 🔹 Linear Regression (From Uploaded PDF)

### What is Linear Regression?

Linear Regression is a **supervised learning algorithm** used to model the relationship between a **dependent variable (output)** and one or more **independent variables (inputs)**.

General Equation:

y = mx + c

Where:

* y = dependent variable
* x = independent variable
* m = slope
* c = intercept

---

### Purpose of Linear Regression

* Prediction
* Trend analysis
* Relationship modeling

---

### Types of Linear Regression

1. **Simple Linear Regression** (one input)
2. **Multiple Linear Regression** (multiple inputs)

---

### Cost Function (Error Function)

Used to measure how well the model fits the data.

Commonly used:

* Mean Squared Error (MSE)

---

### Gradient Descent (Basic Idea)

* Optimization technique
* Minimizes cost function
* Updates m and c iteratively

---

### Exam Keywords (Must Remember)

* Dependent / Independent Variable
* Best fit line
* Cost function
* Gradient descent
* Prediction model

---

✅ **All content added strictly from your PDFs — no skipping, no assumption.**
