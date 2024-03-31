## WHAT IS IT?

RadarSim is a simple model which provides an abstract representation of radar. The goal of this model is to explore how explicitly modeled pulses of energy propagate through the environment and interact with surrounding objects. A single antenna is created at the center of the map, with a user-defined number of target objects placed in random locations. The antenna will emit pulses at a set pulse interval, and “listen” for returns until the next pulse. The antenna is intended to represent an isotropic antenna, emitting uniformly in all directions. The target objects are assumed to be spheres which reflect energy back to the direction which it originated from.

## HOW IT WORKS

The RadarSim model is centered around radar energy and how it propagates through space. This effect is achieved by having each patch carry an energy value, which changes when an antenna emits a pulse, or when a target object reflects energy. When either of those two events occur, the antenna or target assigns itself as a 'source', which then influences the direction in which the energy will propagate from. As energy propagates from a single source patch, it interacts with its neighboring patches to then "pass on" some residual amount of energy to them. Patches can only perform this handoff with patches who are further away from the energy source, therefore creating the effect of energy being transmitted outward from its origin. 

It is important to note that during the transfer of energy between patches, a very small value must be chosen for the signal decay factor. Although the simulation is an abstraction and does not represent the speed of electromagnetic waves, the energy should pass through each patch as quickly as possible to achieve a reasonably similar effect. If the signal decay factor is too large, the energy will linger within each patch and produce undesirable effects.

When the antenna receives a reflected pulse, it will measure the time elapsed since the last emission to determine the duration of how long the wave travelled.

## HOW TO USE IT

The RadarSim interface is fairly simple and provides few controls to the user. Those inputs include:

- Signal-decay-factor: How quickly the energy will decay in each patch
- Propagation-strength: Roughly translates to the transmitted power of the signal
- Pulse-interval: How frequently the antenna will emit a new pulse (ticks)
- Detection-threshold: How high the returned energy value must be for the antenna to consider it a detection
- Num-targets: The number of target objects created on setup

## FUTURE WORK

The current implementation of this model leaves significant room for 
improvement. Improvements include:

- Improved propagation system. The current method of patch/neighbor interaction and relationship with the assigned energy source produces undesirable effects in certain situations.
- Greater directional control / shaping of energy and aspects such as antenna gain.
- Radar ranging based on the recorded time elapsed between transmit/receive of pulses.
- Moving targets, and target speed & direction analysis based on target motion over time.
