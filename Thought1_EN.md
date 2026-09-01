# Field-Convergent Latent Variables: A New Computational Paradigm for Embodied Intelligence

**—A brainstorm summary starting from a brazier, football, and the curveball**

---

## Abstract

This paper systematically argues why mainstream embodied intelligence approaches fundamentally fail in open physical environments, and proposes a new computational paradigm—"Field-Convergent Latent Variables." Key points summarized:

1. The physical world is an ecological state, not a physical state: open environments are multiscale, strongly coupled, dynamically evolving field systems that cannot be exhaustively enumerated by finite-element analysis.
2. Discrete digital systems are intrinsically unable to handle superposition and interference of potential fields in continuous time; the resulting computational complexity is intractable in open environments.
3. Introducing a simulation system is not merely a performance improvement but a fundamental shift in cognitive paradigm: it makes physical laws themselves the computational process, thereby circumventing the curse of discrete enumeration.
4. Field-convergent latent variables are the convergence states of a simulation matrix under intent constraints; they replace traditional decoupled latent variables and become the true causal representation units.
5. The essence of embodied learning is not to remember physical quantities but to remember "feelings"—i.e., the holistic signature of field-convergent latent variables. This provides a minimal operational definition for machine "intuition." 

---

## Chapter 1: Why the problem is unsolvable

### 1.1 Starting from the brazier: the incompressibility of multidimensional intentions

Imagine a scene: a robot is carrying a brazier. Suddenly, a piece of charcoal in the brazier cracks from thermal stress, throwing sparks that land on the carpet.

How do conventional solutions handle this?

**Solution A: Single-task objective.** The robot's goal is to "keep the brazier level." In a reinforcement learning framework, the reward is set so that the smaller the tilt the better. When the charcoal explodes and the carpet catches fire, ...

**Solution B: Weighted multi-objective.** Engineers add "prevent fire" into the reward function with some weight. For example R = w_1 · (brazier stability) + w_2 · (carpet safety). But choosing weights doesn't solve ...

What's the problem?

It is not a matter of the numerical values of weights, but a structural issue. In the real world, these multiple objectives are not comparable in the same dimensional units:

- "Keeping the brazier level" is a posture-stability constraint;
- "Preventing a fire" is a thermodynamic safety constraint;
- "Avoid dropping the brazier and causing a larger fire" is a counterfactual causal-chain constraint.

They activate simultaneously, evolve in parallel, and shape each other's feasible space. Biological systems never merge these objectives into a single scalar and then optimize; instead, they let them compete in parallel in the physical field, with reality itself ...

This is the true meaning of the "multidimensional-intent game": not multi-objective optimization, but multiple intents interfering as potentials on the same physical substrate.

### 1.2 The environment is an ecology, not a physical state

Classical physics simulators (MuJoCo, Isaac Sim, NVIDIA PhysX) operate on a "physical state": given initial and boundary conditions, they use finite elements or explicit integration to solve the system's evolution step by step.

But the environment robots face is never a physical state.

**Features of a physical state:** closed system, enumerable boundary conditions, definable variables, predictable solutions.

**Features of an ecological state:** open system, multiscale coupling, nonlinear feedback, emergence.

The micro-crack in the charcoal, the thermal decomposition temperature of the carpet fibers, local fluctuations in air velocity, the airflow disturbances caused by the robot's movement—these factors from different scales simultaneously infiltrate the same event, and each scale ...

- requires infinitely fine mesh subdivision;
- requires infinitely accurate parameter measurement;
- requires infinitely long computation.

This is the fundamental dilemma of "infinite-element convergence": the more precisely you model it, the further you are from reality.

### 1.3 Why LLMs are doomed to fail

Large language models have shown astonishing capabilities in symbolic reasoning, text generation, and logical inference. So it is natural to think: plug an LLM into a robot so it can "understand" and "decide" ...

This is a category error.

LLMs operate on discrete symbols. Their reasoning is autoregressive, serial, token-by-token. Their time scale is the cadence of token generation, tens to hundreds of tokens per second. Their bandwidth is ...

But the physical world's coupled fields have these characteristics:

- continuous time: variables evolve continuously at every instant rather than at discrete steps;
- parallel coupling: vision, touch, force, inertia, and environment response occur simultaneously across channels, not sequentially;
- millisecond-level causality: a change of direction on a football field or an evasive move at a brazier can have a window of only a few hundred milliseconds. By the time an LLM "finishes thinking," the event on the ground may already be over.

Language is low-bandwidth. Symbols are low-fidelity. Serial processing is slow.

Using an LLM to directly control a robot is like using Morse code to instruct a pianist to perform Liszt in real time—the information is still in transit when the music has already ended.

---

## Chapter 2: Why a simulation system is necessary

### 2.1 Computation is not "describing physics" but "becoming physics"

The core logic of digital computers is: express physical laws as algorithms, discretize physical states into numbers, and iteratively approximate solutions.

The core logic of analog circuits is entirely different: an analog circuit is itself a physical system. Voltage and current evolution do not proceed through algorithms; they directly follow Kirchhoff's laws, Maxwell's equations, and thermodynamic principles ...

When you set a voltage gradient in an analog circuit, currents flow, capacitors charge and discharge, inductors generate back EMF—this is not "simulating physics," this is physics happening.

This implies:

- zero abstraction loss: there's no need to discretize differential equations because the circuit itself is continuous;
- natural parallelism: hundreds of thousands of analog units evolve simultaneously, without clock synchronization or waiting;
- physical time scale: convergence occurs on real physical time, not some slow simulated time.

An analog system is not "computing physics"—it is "doing physics."

### 2.2 "Discrete for discrete, linear for linear"—a fundamental architectural divide

Digital systems and analog systems each have an ontologically irreducible status:

| Dimension | Digital discrete systems | Analog continuous systems |
|---|---:|---:|
| Time | discrete steps | continuous time |
| Parallelism | pseudo-parallel (clocked) | intrinsic parallelism |
| Numerical precision | high numerical precision | physical precision (includes noise) |
| Symbolic abstraction | strong (language, logic) | weak |
| Physical coupling | indirect (requires sensors to digitize) | direct (voltage is the physical quantity) |
| Possibility enumeration | strong (big models, search trees) | weak |

The key question is how to divide responsibilities.

Our answer is clear:

- Digital systems are responsible for "possibilities": enumerating physical knowledge, experience scenarios, counterfactual hypotheses, and tactical planning. They output not actions but candidate wave sources—a set of intent vectors and constraint parameters;
- Analog systems are responsible for "reality": receiving the digital system's output as initial conditions, allowing multiple potential fields to evolve and interfere under physical laws, and finally yielding a uniquely executable action.

This is "discrete for discrete, linear for linear." Neither replaces the other; each handles its own domain.

### 2.3 Programmable analog array: from concept to engineering path

Our core hardware concept is a Programmable Analog Computing Unit (PACU) array—a large analog matrix composed of operational amplifiers and programmable waveform generators.

Each PACU can be configured as a physical solver for a class of differential equations (diffusion, wave, elasticity, heat conduction, etc.). The digital system outputs configuration parameters and initializes these units; the analog matrix then ...

This is not inventing new devices but recombining existing technologies:

- Field-programmable analog arrays (FPAA): they already exist but are small and low precision;
- Neuromorphic chips (Intel Loihi, IBM NorthPole): they demonstrate event-driven asynchronous computation feasibility;
- In-memory computing: already shows energy-efficiency advantages by performing multiply-accumulate in storage.

What is missing is an architectural blueprint unifying these technologies, and our discussion aims to draw that blueprint.

---

## Chapter 3: The emergence of field-convergent latent variables

### 3.1 A phenomenological description from the football field

Now replace the brazier with a football field.

On the field, a player makes decisions when not in possession of the ball. LLM-style approaches are: observe teammate and opponent positions, plan a running route, then execute along that route. But this always misses timing, because the football pitch is ...

Observe truly excellent players. Their judgments are not "computed" but emergent:

On a millisecond time scale, the player simultaneously perceives:

- the ball's trajectory and spin;
- opponents' positions, velocities, and body orientations;
- teammates' movement intentions;
- available space toward the goal;
- their own stamina reserves;
- the strategic significance of the scoreline.

These perceptions are not independent inputs; they blend into a potential field within the player-body-environment system. When the ball approaches, this field instantly interferes:

- some potentials reinforce each other (a teammate's run resonates with your anticipation);
- some potentials cancel each other (an opponent's tight marking counteracts your forward-insert intention).

Creativity is the player actively changing their own "wave source"—their movement modulates the global interference conditions. They are not seeking a peak in an interference pattern; they are creating a new peak.

Ordinary players see "no way through"; elite players run into the only possible way. That way is the diffraction peak after multi-field cancellation.

### 3.2 The birth of field-convergent latent variables

If running on the football field is a field interference, then what is "that unique way"?

It is not the optimal solution of any single physical quantity. It is not the fastest path, the shortest distance, the maximal open space, or the minimal risk—these single-dimensional optima do not exist in real confrontation. It is the ...

That signature is the field-convergent latent variable.

Traditional latent variables (e.g., in VAEs or causal representation learning) are statistically or structurally decoupled from data. They are static:

- they carry no physical time;
- they do not respond to real-time interventions;
- they do not dynamically evolve with environment and intent changes.

Field-convergent latent variables are completely different:

- they are produced by the simulation matrix's evolution under the current intents and boundary conditions, not decoupled from data;
- they naturally satisfy physical constraints because they are the product of physical processes;
- they support interventions natively: changing the intent or boundary conditions causes the simulation matrix to converge to different states;
- they are inherently multimodal and parallel because potential field superposition happens simultaneously.

Field-convergent latent variables mathematically formalize "feeling."

### 3.3 The curveball: the structure of feeling

When a player first accidentally kicks a curveball, they cannot possibly remember those physical quantities:

- the friction coefficient distribution between foot surface and ball skin;
- the ankle angle change curve of the supporting leg;
- the torque transfer efficiency of trunk rotation;
- the boundary-layer thickness of wind speed across different points on the ball's surface.

These quantities occur within milliseconds and cannot be captured by conscious thought, much less computed in real time.

What players remember is a feeling.

But what is a "feeling"? In this framework, feeling gains a structured definition:

"A feeling is a high-quality field-convergence process that leaves an overall signature inside the system. It contains the coupling pattern of all participating variables at the moment of convergence, compressed in a highly efficient, non-linguistic form."

Afterward, the repeated attempts to "find the feeling" are not reproducing physical parameters but trying to bring the system back into that familiar convergence region. Success or failure depends not on precision of a parameter but on ...

This is how humans learn the curveball. This is how robots can learn physical interaction.

---

## Chapter 4: Why physical states are unsolvable but ecological states are solvable

### 4.1 The illusion of "precision" in physical states

The central belief of the physical-state approach is: if we discretize the physical world finely enough, measure parameters accurately enough, and make integration steps small enough, we can precisely predict the future.

This belief holds in closed systems. Ballistic trajectories, bridge stress distributions, and chip thermal diffusion can be solved to high accuracy by finite element methods.

But open environments are not closed systems.

Material properties in the real world vary spatially; contact microgeometry is unknown; air flow is nonlinear and chaotic. Precise inputs do not exist and precise boundary conditions do not exist. The more you pursue ...

### 4.2 The "computability of emergence" in ecological states

An ecological state can be solvable precisely because it does not pursue exactness.

In ecological systems, each agent does not compute a global optimum. Each agent reacts locally to local information, and the system-level behavior emerges from these local reactions into usable macroscopic patterns.

Biological systems can handle open environments in real time not because they compute faster, but because they outsource computation to the physical world itself.

When water flows over a fish's body, the fish does not need to solve Navier–Stokes to feel flow direction. The fluid pressure field acts directly on the lateral-line sensors; the physical world is doing the real-time computation for the fish.

When a player shifts direction on the field, they do not need to compute the opponent's center-of-mass transfer function. They just "feel" the opponent's potential field in their body and automatically avoid high-potential regions.

### 4.3 This is not "abandoning precision" but "trading for a different precision"

Analog computation has long been dismissed by digital computation as "imprecise and unreliable." 

But precision is relative to what.

Digital systems' precision is relative to the mathematical world: they precisely represent a floating-point number but cannot precisely represent a physical quantity.

Analog systems' "imprecision" is actually physical faithfulness. Noise, drift, and nonlinearity in analog circuits are part of the physical world. When an analog system processes physical problems, these features ...

Analog systems' precision is relative to the physical world—they exist within it, and thus are naturally faithful.

---

## Chapter 5: A structural solution with multi-attention parallelism

### 5.1 The true source of attention: intent is not a filter but a boundary condition

In traditional deep learning, attention is a weighted reallocation across inputs: it assigns weights to features based on "relevance." But it does not know "why" something is relevant.

In our framework, attention is not weighting but an intent-created constraint field in the simulation matrix.

"Keeping the brazier level" is not a weight but a potential well constraint applied in the simulation matrix—the brazier's state must remain in a low-potential region. This constraint is not learned via backpropagation ...

### 5.2 Parallel games of multidimensional intent

In the brazier scenario, at least three intents compete simultaneously:

- keep the brazier level (task intent);
- prevent a fire (safety intent);
- avoid causing a larger fire when extinguishing (counterfactual causal intent).

These intents are irreducible and cannot be merged into a scalar. Traditional approaches compress them into a single reward function and thereby lose information and distort structure.

In our approach, each intent is an independent potential field injected into the simulation matrix. They do not merge or normalize. They evolve and interfere simultaneously on the physical substrate.

The simulation matrix's final convergence state is naturally the result of this multidimensional-intent game. There is no need to design arbitration logic or tune balancing weights. Physical evolution itself is the arbitrator.

### 5.3 Active survival attention boundaries

Why can living systems handle open environments? Because they already know what to pay attention to before acting.

This "knowing" is not a posterior analysis after perception but a priori constraints from intent.

When animals forage, their attention is shaped by hunger intent—they automatically ignore sensory inputs irrelevant to food and focus on cues relevant for energy acquisition. This filtering does not occur in the data-processing layer ...

This is the "active survival attention boundary": intent precedes perception; boundaries precede computation.

Without this boundary, a system must process all inputs and enumerate all possibilities. That is the root cause of discrete systems being intractable in open environments.

With intent boundaries, the infinite-dimensional ecological state is instantly compressed into a finite-dimensional intent-relevant field. The compression does not happen at the algorithmic level but at the system's physical boundaries.

---

## Chapter 6: A complete architectural blueprint

### 6.1 The structure of a layered heterogeneous system

Synthesizing the above, we outline a three-layer architecture:

**Top layer: Digital cognitive system (LLM or similar)**
- Responsibility: intent generation, semantic understanding, experience retrieval, possibility enumeration, pre-action planning.
- Output: a set of candidate intents and corresponding wave-source parameters (initial conditions of physical constraint fields).
- Time scale: seconds to minutes (slow).
- Not part of the real-time control loop.

**Middle layer: Intent compilation and field-memory system**
- Responsibility: compile digital outputs into configuration code for the analog matrix; store historical field-convergent latent variables as "feeling memory"; retrieve the most matching field signatures for the current scene across trials ...
- Output: initial and boundary conditions for the simulation matrix.
- Time scale: milliseconds to seconds (mid-speed).
- This is the "finding-feeling" layer.

**Bottom layer: Simulation-digital hybrid physical convergence matrix**
- Responsibility: receive configuration from the compilation layer; let multiple potential fields evolve in analog circuitry; converge on a low-dimensional signature representing the current ecological state.
- Output: field-convergent latent variables (fed back to the middle and top layers for learning, memory, and subsequent decisions).
- Time scale: microseconds to milliseconds (fastest).
- This is the "doing-physics" layer.

### 6.2 Training closed loop

The training target is not to learn a mapping from physical quantities to actions, but to learn how to compile intents and environmental information into correct boundary conditions for the analog matrix so that the matrix's convergent latent variables correspond to successful actions.

- Random initialization: the matrix produces random convergences;
- Successful experiences: some convergences lead to high-quality actions; these latent variables are stored in field memory;
- Subsequent invocation: under similar intents, retrieve related field memory as initialization to accelerate convergence;
- Failure correction: if convergence is incorrect, adjust compilation parameters (like humans "adjusting feeling").

The system's experience is stored not in weights but in a distribution of "field signatures."

### 6.3 The role of diffusion models

Diffusion models learn probability distributions and perform stepwise denoising in the digital domain. In our architecture, their continuous-time form (SDE/ODE) can act as a translator between the digital and analog domains.

- In offline training, diffusion models learn how to compress high-dimensional multimodal perception into low-dimensional field parameters;
- In online inference, the reverse process of the diffusion model can map the current scene into initialization conditions for the simulation matrix in a single shot;
- The analog matrix then handles subsequent continuous-time evolution, avoiding the computational explosion of multi-step sampling on discrete GPUs.

Diffusion models perform the "one-step translation," while the simulation matrix performs the "physical convergence." Each has its role without overstepping.

---

## Chapter 7: Toward artificial intuition

### 7.1 A minimal operational definition of intuition

From the perspective of field-convergent latent variables, "intuition" gains a precise definition:

"Intuition is the system's ability, given an intent, to rapidly enter a high-probability successful convergence region; that region is shaped by the distribution of historical field-convergent latent variables and can be activated without discrete enumeration."

A football player's intuition is that their sensorimotor-environment system, after countless field convergences, has formed a dense, quickly traversable "feeling landscape." Faced with the field, they do not need to enumerate all possibilities ...

### 7.2 The nonlinguistic and non-symbolic nature of feeling

Feelings cannot be expressed in language because the bandwidth of discrete symbols is too low to carry the continuous signature of fields. But feelings are not unknowable—they can be re-experienced by the simulation system.

When a robot "remembers a feeling," it stores a field signature. When the scene is similar, that signature is reloaded into the simulation matrix, instantly returning the system to that "right" state.

This is the machine version of "finding the feeling."

### 7.3 From training to emergence

As field memory accumulates, the system's behavior undergoes qualitative change: it starts producing actions that were never explicitly trained because in new combinations of intent and environment, interference of multiple old field signatures creates ...

This is machine creativity.

It is not that the system found a new point in the search space; it is that a new interference pattern emerged from the superposition of potential fields.

---

## Conclusion: Why this path must be taken

Digital AI has achieved astonishing success in images, language, and board games—closed systems. But when robots enter the real physical world, we encounter a fundamental barrier:

The physical world is not discrete, linear, or enumerable.

Using digital discrete systems to simulate real physics is essentially trying to solve an "infinite-element" problem with a finite-element approach. This path is computationally intractable and philosophically a category mistake.

The only way forward is to let the physical world compute itself. Analog simulation systems are the material vehicle for this path, and field-convergent latent variables are how a simulation system compresses ecological states under intent guidance into actionable signatures.

They let machines move from "computing physics" to "feeling physics," from "memorizing formulas" to "finding feeling."

That is the whole of our discussion.

---

*A brainstorm that starts from a brazier and ends on a single word: feeling.*
