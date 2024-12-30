# Reinforcement Learning applied to OpenAI's Gymansium Lunar Lander
 
This project, developed for **Introduction to Intelligent and Autonomous Systems**, focuses on understanding basic reinforcement learning concept implementations. Through extensive experimentation, we were also able to train a model capable of landing strictly, while correcting turbulence and wind changes under unstable, challenging circumstances.


The work was carried out by:

 - **Eduardo Passos**
 - **Pedro Fernandes**
 - **Rafael Pacheco**
 
For a general development and results review: **`presentation.html`**

\
**Thank you for exploring this project! You can find the original repository [here](https://github.com/rafa907p/Reinforcement-Learning-Lunar-Lander.git)! 🚀**

---

## Original Problem 

---

- **Environment**: Continuous Lunar Lander environment from Gymnasium.
- **Objective**: Safely land the rocket by optimizing engine usage and trajectory under challenging conditions like wind, turbulence, and variable gravity.

### State and Actions
- **State**: 8-dimensional vector containing:
  - Lander coordinates
  - Linear velocities
  - Angle and angular velocity
  - Boolean indicators for leg-ground contact
- **Actions**:
  - `0`: Do nothing
  - `1`: Fire left orientation engine
  - `2`: Fire main engine
  - `3`: Fire right orientation engine

### Rewards
- Reward metrics include:
  - **Penalties**: High velocity, excessive engine use, angular deviations, and long episode durations.
  - **Bonuses**: Both legs touching the ground, proximity to landing site, and stable landings.

---

## Modified Problem

---

### Environment Changes
- Introduced variable wind, turbulence, and gravity.
- Ensured adaptability for unstable and theoretical landing scenarios.

### Agent Adjustments
Added penalties for:
  - Excessive main engine usage (fuel management).
  - Angular deviation (stability).
  - Prolonged episode duration (efficiency).

Added observation noise and a partial observability scenario.

## Chosen Algorithm

The algorithm was chosen after carefully comparing DDPG, TD3 and SAC performance and complexities.

We chose **TD3**:

- Designed for **continuous action spaces**.
- Improves upon DDPG by addressing overestimation bias and training instability.
- A middle ground between the simplicity of DDPG and computational cost of SAC.



## Hyperparameter Tuning
Used **Optuna** for optimization:
- Learning Rate
- Batch Size
- Tau (soft update factor)
- Gamma (discount factor)
- Replay Buffer Size

## Results

### Performance Metrics
- **Original Environment**:
  - Average Reward: 115.85
  - Standard Deviation: 128.38
  - Episodes with Reward ≥ 200: 208/500
- **Custom Environment**:
  - Average Reward: 10.77
  - Standard Deviation: 90.75
  - Episodes with Reward ≥ 200: 44/500

### Observations
- Custom environment reduces reward variance and improves agent consistency.
- Enhanced agent behavior includes better fuel management and faster decision-making.

## Conclusion

### Key Takeaways
- The improved TD3-based agent excels in fuel management, decision speed, and consistency.
