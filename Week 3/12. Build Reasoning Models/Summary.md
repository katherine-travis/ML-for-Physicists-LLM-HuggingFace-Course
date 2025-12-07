# Chapter 12 Summary: Build Reasoning Models

This chapter covers the basics of reinforcement learning and its role in LLMs through exploration of Open R1. LLMs are good at many generative tasks, but, until recently, they exhibited poor performance on reasoning problems.

## Introduction to Reinforcement Learning

Reinforcement learning involves training an agent that learns from environment feedback. While LLMs are excellent at predicting the next word through pretraining on large amounts of text, this doesn't necessarily make them good at providing useful information, avoiding biased content, or responding naturally and engagingly. There are 5 key components to reinforcement learning:

-Agent: This is the learner. For LLMs, the LLM is the agent we want to train

-Environment: The environment provides feedback to the agent. For LLMs, this could be the user it interacts with, or a simulated scenario.

-Action: These are the choices the agent can make in the environment. 

-Reward: This is the feedback the agent receives after taking an action. Rewards are usually numbers.
&emsp -Positive rewards reinforce an action
&emsp -Negative rewards are penalties that discourage an action

-Policy: This is an agent's strategy for choosing an action. It sets a function that tells the agent what action to take in different situations. As the agent learns, the policy becomes better at choosing actions that lead to higher rewards.

Reinforcement learning happens through trial and error. First, the agent observes the environment, then it takes action, receives feedback about the action, and finally updates policy based on the reward. This process is iteratively repeated.

Reinforcement learning from human feedback uses human feedback as a proxy for the reward signal. Human preference data is used to train a reward model that learns to predict what kinds of responses humans will prefer. The reward model is then used to fine-tune the LLM.

## Understanding DeepSeek R1

Deepseek represents a significant advancement in developing reasoning capabilities through reinforcement learning. A new reinforcement algorithm called group relative policy optimization (GRPO) is introduced. The goal of this paper was to explore whether pure reinforcement learning could develop reasoning capabilities without supervised fine-tuning, departing from the standard approach requiring supervised fine-tuning. The R1-Zero model made initial attempts, recognize errors or inconsistencies, and adjust approaches based on recognition and explain why new approaches are better. This emerged naturally from RL training without explicit programming, demonstrating learning rather than memorization. Deepseek R1 expanded upon this by prioritizing both reasoning performance and usability through multiple training phases. The reasoning RL focuses on developing core reasoning capabilities across mathematics, coding, science, and logic domains.

## GRPO

Reinforcement learning involves training an agent that learns from environmental feedback. Reinforcement learning from human feedback (RLHF) requires collecting human preference data comparing different generated responses. Group Relative Policy Optimization directly evaluates model generated responses by comparing them within groups of generation to optimize the policy of the model, rather than training a separate value model. A reward score is assigned to each generated response. Outputs within the same group are compared. Using standardization allows the model to assess each response's performance. Advantage values greater than 0 is better than average while advantage values less than 0 are worse than the average. The advantage values are fed to a target function for policy update. The policy update uses a clipped objective function with a KL divergence penalty to ensure stable learning. The Transformer Reinforcement Learning library provides practical GRPO implementation through the GRPO Trainer class. 
