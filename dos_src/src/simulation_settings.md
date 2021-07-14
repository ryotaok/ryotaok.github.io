# Simulation Settings

Characters:

- All characters up to version 2.0 are implemented (you can choose a preferable version for simulation).
- Using stats of character level at 90.
- All talent levels are 10.
- Constellations are limited to 0 for now.

Weapons:

- Most weapons up to version 2.0 are implemented (you can choose a preferable version for simulation).
- Using stats of weapon level at 90.
- All five star weapons have the refinement rank of 1, while all four star weapons have the refinement rank of 5. Some three star weapons are included.

Artifacts:

- Most artifacts up to version 2.0 are implemented (you can choose a preferable version for simulation).
- All the artifacts have the same stats: 80 ATK%, 80% Crit Rate, 311 flat ATK, 46.6% or 58.3% DMG bonus for the respective character's vision. If the sum of Crit rate exceeds 80%, the excesses are converted to Crit damage.

Damage calculation:

- Most in-game features are implemented (see the Limitations below): enemy resistance, enemy defense, elemental reactions, internal cooldown of elemental application, the gauge unit theory,
- Critical damage is an expected value of Crit rate and Crit damage.
- Randomness of passive effects is always 100% (for example, Prototype Archaic has 50% chance to activate its passive but it is always activated when its condition is met).

Simulated field:

- The enemy is a hilichurl at level 90.
- Simulated characters try to take actions every 200 milliseconds and the simulation ends when the simulation timer is at 20 seconds (these values can be changed). If the actions are under cooldown, the characters will do nothing.
- The first character has an attacker role, where the elemental burst, the elemental skill, and the normal or charge attack are taken. While the rest of the characters, if exists, have supporter role, where only the bursts and the skills are taken.
- Characters recharge all the their energy at the begging, and 15 energy are given when the timer is at 5 seconds.

Other implementation limitations:

- The enemy has infinite HP and does not move.
- Characters have infinite stamina.
- Shields are always active.
- When characters use Staff of Homa, their HP is below 50%.
- Amos' Bow travels the maximum distance.
- Elemental resonance is not implemented.
