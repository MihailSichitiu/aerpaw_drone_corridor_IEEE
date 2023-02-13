# aerpaw_drone_corridor_IEEE
Drone corridor docker experiment code

The code was developed by John Kesler (jckesle2@ncsu.edu) and was migrated from the NCSU github (github.ncsu.edu) to this repository.

Air corridors are considered as a promising solution to traffic management of a large number of aircrafts (both manned and unmanned). To enable such a system, we developped an emulation of an air corridor system based on a software in the loop (SITL) from ArduPilot (a popular open source autopilot).

In this demonstration, several UAVs are instructed to take-off and cross through a relatively narrow air corridor (only one UAV can pass through safely at a time). To make things interesting, after the UAVs start to pass through the corridor, the corridor is externally closed (and the UAVs are informed), and an alternate corridor is opened. The demo shows how the UAVs re-route through the new corridor.

In this system the UAVs route to their destination autonomously through the air corridor while coordinating with the other UAVs (by maintaining a minimum distance of two grid units to all other UAVs). The air corridors are defined as a three-dimensional grid where an UAV occupying a grid location can travel at any of the 26 adjacent locations as long as it is at least one step away from all other UAVs.

Due to the realistic parameters of the emulation (e.g., turbulence, timing of the take-off commands, etc.), the emulation results may change slightly from one run to the other.

The system features a visualization system based on Google Earth, showing in real time both the air corridor (as a white mesh of allowed space to be traversed), as well as the location of the UAVs.

The entire system runs from a docker compose file that sets up a docker container for each UAV, and an additional one for the ground coordinator (which is the entity that communicates the availability or lack thereof for the air corridors).
