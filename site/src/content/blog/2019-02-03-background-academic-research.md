---
title: Background Academic Research
description: "Surveying academic papers on game-playing AI, from NEAT and DeepMind Lab to Mario AI competitions."
pubDate: 2019-02-03
---

In order to stand on the shoulders of giants in academia, we must know who has come before us. To accomplish this, I first compiled a list of academic research papers that seemed like they might be relevant to my research interests:

- The 2010 Mario AI Championship: Level Generation TrackOn Game Art, Circuit Bending and Speedrunning as Counter-Practice: 'Hard' and 'Soft' Nonexistence
- From NES-4021 to moSMB3.wmv: Speedrunning the Serial Interface
- A Practiced Practice: Speedrunning Through Space With de Certeau and Virilio
- Some Studies in Machine Learning Using the Game of Checkers
- Constraint-based generalization: learning game-playing plans from single examples
- The Parti-game Algorithm for Variable Resolution Reinforcement Learning in Multidimensional State-spaces
- Learning To Play the Game of Chess
- Temporal difference learning applied to a high-performance game-playing program
- An Empirical Study of Machine Learning Algorithms Applied to Modeling Player Behavior in a "First Person Shooter" Video Game
- Real-time neuroevolution in the NERO video game
- Machine learning in digital games: a survey
- Action-Conditional Video Prediction using Deep Networks in Atari Games
- DeepMind Lab
- The 2009 Mario AI Competition
- The Mario AI Benchmark and Competitions
- The 2010 Mario AI Championship: Level Generation Track
- Evolving Neural Networks through Augmenting Topologies
- StarCraft II: A New Challenge for Reinforcement Learning
- TStarBots: Defeating the Cheating Level Builtin AI in StarCraft II in the Full Game
- The Current State of StarCraft AI Competitions and Bots
- On Reinforcement Learning for Full-length Game of StarCraft
- Multiagent Bidirectionally-Coordinated Nets: Emergence of Human-level Coordination in Learning to Play StarCraft Combat Games
- StarCraft as a Testbed for Engineering Complex Distributed Systems Using Cognitive Agent Technology
- General Video Game AI: Competition, Challenges and Opportunities
- Rapid and Reliable Adaptation of Video Game AI
- Monte-Carlo Tree Search: A New Framework for Game AI
- Pogamut 3 Can Assist Developers in Building AI (Not Only) for Their Videogame Agents
- Game AI revisited
- Mind games [computer game AI]
- Rapid adaptation of video game AI

I then narrowed this list down to the 5 most relevant documents.

[DeepMind Lab](https://arxiv.org/pdf/1612.03801.pdf) documents the DeepMind team's development of a platform for testing AI in perceptually and physically rich environments. They posit that an agent can be sufficiently trained given only RGB data and reward. Velocity information can be useful. The agent can interact with its environment by moving in 6 axes and rotating its point of view. This is encouraging for my research, as I might be able to directly interpret monitor output for my game without doing anything special.

[Evolving Neural Networks through Augmenting Topologies](http://nn.cs.utexas.edu/downloads/papers/stanley.ec02.pdf) provides a comprehensive description and analysis of NeuroEvolution of Augmented Topologies (NEAT), a refined method for generating neural networks. It shows that by using historical markings, protecting innovation through speciation, and incrimentally growing from minimal structures instead of random initial structure is much more efficient than previous alternatives. While this paper does not specifically relate to video games, it was the foundation of [SethBling](https://www.youtube.com/channel/UC8aG3LDTDwNR1UQhSn9uVrw)'s AI project, [MarI/O](https://www.youtube.com/watch?v=qv6UVOQ0F44), so I thought it was worth reading.

[General Video Game AI: Competition, Challenges, and Opportunities](https://www.aaai.org/ocs/index.php/AAAI/AAAI16/paper/view/11853/12281) gives an account of the General Video Game AI (GVGAI) Competition. This competition has contestants develop AI with the intention of successfully playing a wide variety of 2D video games without being provided a rule set. Results were inconclusive, with winning bots using a variety of techniques such as evolutionary algorithms, random walks, A*, and others. Clearly there is a lot of work to be done in this field.

[The Mario AI Benchmark and Competitions](https://ieeexplore-ieee-org.proxy.lib.umich.edu/document/6156425) shows the synopsis of a competition for AI developers to create an agent that can play Super Mario Bros the best. The results showed that the A* based agents performed the best, outclassing machine learning agents. However, this proved to not be the case for the competition the next year that included more complex mechanics. A* techniques could be worth exploring for my TASBot generator, but machine learning is likely going to be more effective for high complexity games.

[Real-time neuroevolution in the NERO video game](https://ieeexplore-ieee-org.proxy.lib.umich.edu/document/1545941) demonstrates how NEAT can be used in real time (rtNEAT) and applied to video game AIs. This article was interesting because it directly tied NEAT to video games, but it might not be very relevant to my interests. TASBot generation does not need to run in real time, it has plenty of time to run the full NEAT algorithm before finalizing the route.
