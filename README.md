# Push Block

## Installation

In Unity 2019.4 or later, open the Package Manager, hit the "+" button, and select "Add package from git URL".

![Package Manager git URL](https://github.com/Unity-Technologies/ml-agents/blob/release_20_docs/docs/images/unity_package_manager_git_url.png)

In the dialog that appears, enter
 ```
git+https://github.com/Unity-Technologies/ml-agents.git?path=com.unity.ml-agents#release_20
git+https://github.com/Unity-Technologies/ml-agents.git?path=com.unity.ml-agents.extensions#release_20
```

## Basic Push Block

![Push](push.png)

- Set-up: A platforming environment where the agent can push a block around.
- Goal: The agent must push the block to the goal.
- Agents: The environment contains one agent.
- Agent Reward Function:
  - -0.0025 for every step.
  - +1.0 if the block touches the goal.
- Behavior Parameters:
  - Vector Observation space: (Continuous) 70 variables corresponding to 14
    ray-casts each detecting one of three possible objects (wall, goal, or
    block).
  - Actions: 1 discrete action branch with 7 actions, corresponding to turn clockwise
    and counterclockwise, move along four different face directions, or do nothing.
- Float Properties: Four
  - block_scale: Scale of the block along the x and z dimensions
    - Default: 2
    - Recommended Minimum: 0.5
    - Recommended Maximum: 4
  - dynamic_friction: Coefficient of friction for the ground material acting on
    moving objects
    - Default: 0
    - Recommended Minimum: 0
    - Recommended Maximum: 1
  - static_friction: Coefficient of friction for the ground material acting on
    stationary objects
    - Default: 0
    - Recommended Minimum: 0
    - Recommended Maximum: 1
  - block_drag: Effect of air resistance on block
    - Default: 0.5
    - Recommended Minimum: 0
    - Recommended Maximum: 2000
- Benchmark Mean Reward: 4.5

## Cooperative Push Block

![CoopPushBlock](cooperative_pushblock.png)

- Set-up: Similar to Push Block, the agents are in an area with blocks that need
to be pushed into a goal. Small blocks can be pushed by one agents and are worth
+1 value, medium blocks require two agents to push in and are worth +2, and large
blocks require all 3 agents to push and are worth +3.
- Goal: Push all blocks into the goal.
- Agents: The environment contains three Agents in a Multi Agent Group.
- Agent Reward Function:
  - -0.0001 Existential penalty, as a group reward.
  - +1, +2, or +3 for pushing in a block, added as a group reward.
- Behavior Parameters:
  - Observation space: A single Grid Sensor with separate tags for each block size,
    the goal, the walls, and other agents.
  - Actions: 1 discrete action branch with 7 actions, corresponding to turn clockwise
    and counterclockwise, move along four different face directions, or do nothing.
- Float Properties: None
- Benchmark Mean Reward: 11 (Group Reward)
