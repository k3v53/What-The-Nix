---
draft: true
---


# Installing Software Through Programs

# Installing Software Through Packages

## Determine the location of the packages

# Difference Between Programs, Packages and Services

Nix has a way to distinguish different types of software, those are:

- [[Programs]]: These are programs that you install in your device that are [[Daemonless]] and has extra configuration options to define, like [[GameScope]], [[Git]], etc.
- [[Services]]: These are programs that are known to be running in the background as a daemon. They also include extra configuration options to set up to your liking.
- [[Packages]]: These are a group of things that contains the necessary libraries for a program to run, they can be programs, services or simple dependencies, and they don't have a standarized way to receive configurations, some of them have configurations with the [[Home Manager]] module, but some others just plain don't have and you have to write them yourself.

The rule of thumb is simply looking your desired software from [[Programs]], if it is not listed there search it on [[Services]], and finally [[Packages]].