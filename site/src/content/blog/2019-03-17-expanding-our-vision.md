---
title: Expanding our Vision
description: "Optimizing CelesteBot's vision system from 10x10 to 30x30 tiles through collision caching, and fixing entity detection bugs."
pubDate: 2019-03-17
---

This week I wanted to focus on improving the vision for [CelesteBot](https://github.com/sc2ad/CelesteBot/tree/qlearning).

As noted in the last post, 10x10 vision worked fine but anything much bigger tanked the game's frame rate. I looked at what the mod was doing behind the scenes, and it turns out the method for building the bot's vision was checking for collisions in each tile every frame. Collisions are one of the most expensive calculations in games, so you definitely don't want to check for collisions this often. Most game content in Celeste is static, so I decided to try caching this information after collision detection was done. The difference was immediate and significant. Here are the frame rates for the game before and after caching:

- Before:
  - 10x10: 60 FPS
  - 12x12: 15 FPS
  - 15x15: 2 FPS
  - 20x20: 1 FPS
  - 30x30: 1 FPS
- After:
  - 10x10: 60 FPS
  - 12x12: 60 FPS
  - 15x15: 60 FPS
  - 20x20: 60 FPS
  - 30x30: 60 FPS

Undoubtedly there will be some modifications needed in later levels for game entities that move, but this is entirely doable.

I also noticed a bug not previously caught: the bot vision was only detecting generic "entities". It should have been distinguishing wall tiles and spikes as different values within the matrix, but the code wasn't able to see SolidTiles or Spikes. I modified the entity fetching code a little to check what kind of entity was being collided with. It checks each entity for collisions, then chooses the colliding entity with highest priority. The priority is currently Entity \< Tile \< Spike. In addition to this modification, I removed the player from the bot's vision. The player is always at the center of vision, so there is no need to render them.

This change revealed another bug: spikes were not being detected at all. The collision detection was being done with a single point at each tile. I decided to try checking collisions for collisions within a square the size of a tile, and suddenly spikes were detectable.

I also made a minor performance improvement. Previously, the bot's vision was being rendered by a set of circles. This was inefficient and tanked the frame rate with large vision grids. I changed the circles into small squares, and now the frame rate is a steady 60 even with 30x30 vision.

Finally, I decreased the death timer from 2.5 to 2.2 seconds. This appears to be fast enough that the player can't die again before the time has elapsed. Although, it may need to be changed for later levels.

With all these changes in place, I ran NEAT overnight for 200 generations, a process that took about 12 hours. The results were interesting, but mostly unsuccessful. The main problem is that 30x30 = 900, which is a lot of inputs for NEAT to experiment with by iterating through them. It is good for the bot to be able to see this region, but it makes the bot take much longer to learn anything. The other problem was a bug present at 1:49:00. The mod failed to reset the level before running the next organism, resulting in an artificially high fitness for an organism that did not deserve it. NEAT then continued to cling to this type of species for the rest of the simulation, with poor results. I'm still not sure why this occurred, I tested the death timer duration after this simulation and it reset properly every time. If this occurs again, I'll need to do a more thorough investigation.

<iframe width="560" height="315" src="https://www.youtube.com/embed/aVTlBXTexzM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Now that the expanded vision is in place, it's time to think about how to get as much training time as possible for the bot. I would like to investigate methods of speeding up Celeste's physics. Another useful feature would be the ability to save and load the genome data so that sessions can be carried over between game launches. These will be the main focus of next week's work.
