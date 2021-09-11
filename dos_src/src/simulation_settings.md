# Simulation Settings

Characters:

- All characters up to version 2.1 are implemented.
- Using stats of character level at 90.
- All talent levels are 10.
- Constellations are limited to 0 for now.

When a player presses some button to do a certain action, it does not always mean that the enemy takes damage. There are differences between character's actions and their attack entities (which have a hit box in the game). The player interactions to character's actions are considered as `AttackEvent`, and attack entities that can damage enemies are considered as `Attack`.

In this program, most of `Attack` are crated by characters at the same time as `AttackEvent` is triggered but some are not, especially those have DoT damage over times. Normal and charge attacks are simultaneous.

Weapons:

- Most weapons up to version 2.1 are implemented.
- Using stats of weapon level at 90.
- All five star weapons have the refinement rank of 1, while all four star weapons have the refinement rank of 5. Some three star weapons are included.

Artifacts:

- Most artifacts up to version 2.1 are implemented.
- All the artifacts have the same stats: 80 ATK%, 80% Crit Rate, 311 flat ATK, 46.6% or 58.3% DMG bonus for the respective character's vision. If the sum of Crit rate exceeds 80%, the excesses are converted to Crit damage.

Damage calculation:

- Most in-game features are implemented: enemy resistance, enemy defense, elemental reactions, internal cooldown of elemental application, the gauge unit theory, stamina,
- Critical damage is the average value of Crit rate and Crit damage.
- Randomness of passive effects is always 100% (for example, Prototype Archaic has 50% chance to activate its passive but it is always activated when its condition is met).

The simulated field:

- The enemy is a hilichurl at level 90.
- Simulated characters try to take actions every 200 milliseconds and the simulation ends when the simulation timer is at 20 seconds (these values can be changed). If the actions are under cooldown, the characters will do nothing.
- The first character has an attacker role, where the elemental burst, the elemental skill, and the normal or charge attack can be used. While the rest of the characters, if exists, have supporter role, where only the bursts and the skills can be used.
- Characters recharge all the their energy at the begging, and 15 energy are given when the timer is at 5 seconds.

Other implementation limitations:

- The enemy has infinite HP and does not move.
- Shields are always active.
- When characters use Staff of Homa, their HP is below 50%.
- Amos' Bow travels the maximum distance.
- Elemental resonance is not implemented.
- The results of the future characters are not accurate.
- Healing bonus is not implemented (most healing related features are not implemented yet).
- Geo Construct.
- Plunge attacks are considered as charge attacks without stamina consumption for now.

Some restrictions of the ranking:

- The following weapons are not used by supporters: Staff of Homa, Crescent Pike, Prototype Crescent, Rust.

## Progress of implementations

Each blank cell means that the respective feature is correct. Although most charge attacks are not implemented, the cells are left blank.

Characters:

For Anemo characters, I think elemental absorption works correctly.

| Name               | Normal attack       | Charge attack                        | Press skill                                          | Hold Skill                  | Burst                                        | Other passives (and alternate sprint)                          |
| --                 | --                  | --                                   | --                                                   | --                          | --                                           | --                                                             |
| Raiden Shogun      | WIP                 |                                      | Burst DMG bonus may be incorrect                     |                             | Starting 40 resolve stacks and Incomplete    |                                                                |
| KujouSara          | WIP                 |                                      | Incomplete                                           |                             | Incomplete                                   |                                                                |
| Aloy               | WIP                 |                                      | May be incorrect                                     |                             |                                              |                                                                |
| Ayaka              |                     |                                      |                                                      |                             | 15 hits in total                             | A4 bonus and infusion are always active                        |
| Yoimiya            | WIP                 |                                      | Improves NA multipliers by 161.74%                   |                             | Aurous Blaze triggers every 2 seconds        |                                                                |
| Sayu               | WIP                 |                                      | Incomplete                                           |                             | Incomplete                                   |                                                                |
| Kazuha             |                     |                                      |                                                      |                             |                                              | A4 improves DMG bonuses of Pyro, Hydro, Electro, Cryo elements |
| Yanfei             |                     | Used if at least 3 Scarlet Seals     |                                                      |                             |                                              | CA always triggers A4                                          |
| Eula               |                     |                                      |                                                      | Used if 2 Grimhearts        |                                              | A4 does not reset CD of skills                                 |
| Rosaria            |                     |                                      |                                                      |                             |                                              | A1 bonus applies on cast                                       |
| Xiao               | WIP                 | WIP                                  | Generate particles even if burst is on?              |                             |                                              | A4 is not implemented                                          |
| HuTao              |                     | Stamina consumption may be incorrect | Blood Blossom applies on cast                        |                             |                                              | A4 bonus is always active                                      |
| Albedo             |                     |                                      |                                                      |                             | 3 DoT hits                                   | A1 is not implemented because of infinite HP                   |
| Ganyu              |                     | Always used                          |                                                      |                             |                                              | A4 applies to all characters                                   |
| Tartaglia          | Always Melee Stance |                                      | Incomplete                                           |                             |                                              | Master of Weaponry increases all NA multipliers by 5%          |
| Diona              |                     |                                      |                                                      |                             | Incomplete                                   | Both A1 and A4 are not implemented                             |
| Zhongli            |                     |                                      |                                                      | Never used                  |                                              | Both A1 and A4 are not implemented                             |
| Xinyan             |                     |                                      | On hit, the shield level 3 is always activated       |                             |                                              | A4 applies to all characters                                   |
| Amber              |                     | Always used                          | The puppet explodes immediately                      | Never used                  | 18 hits                                      | A4 is active without the weakpoint                             |
| Bennett            |                     |                                      |                                                      | Never used                  |                                              | TODO A4                                                        |
| Xiangling          |                     |                                      |                                                      |                             |                                              | A4 applies to the first member                                 |
| Diluc              |                     | Never used                           | Starting 3 charges                                   |                             | 3 DoT hits                                   |                                                                |
| Klee               |                     | Incomplete                           | Starting 2 charges, mines hit 2 times for each skill |                             | 24 hits in total                             | Both A1 and A4 are incomplete                                  |
| Barbara            |                     |                                      | Not implemented                                      |                             | Not implemented                              | Both A1 and A4 are not implemented                             |
| Mona               |                     |                                      |                                                      |                             | May not be complete                          | A1 is not implemented                                          |
| Xingqiu            |                     |                                      | Incomplete                                           |                             | Triggers every 1.233 seconds                 | A1 is not implemented                                          |
| Beidou             |                     |                                      | Incomplete                                           |                             | Targets only one enemy                       | May not be complete                                            |
| Fischl             |                     |                                      | Generate a particle for every attack                 |                             | Reset CD of the skill                        | A4 may not be correct                                          |
| Keqing             |                     |                                      |                                                      | Never used                  |                                              |                                                                |
| Lisa               |                     |                                      |                                                      | Used if 3 Conductive Status | 28 hits                                      |                                                                |
| Razor              |                     |                                      | Generate particles even if burst is on?              |                             | Reset CD (WIP)                               |                                                                |
| Chongyun           |                     |                                      | Infuse for only himself                              |                             |                                              | A1 applies to all characters                                   |
| Kaeya              |                     |                                      |                                                      |                             | 12 hits in total                             | A1 does not heal                                               |
| Qiqi               |                     |                                      | Incomplete                                           |                             | Incomplete                                   | Incomplete                                                     |
| Jean               |                     |                                      |                                                      |                             | Incomplete                                   | Incomplete                                                     |
| Sucrose            |                     |                                      |                                                      |                             |                                              | A1 may be incorrect                                            |
| Traveler (Anemo)   |                     |                                      |                                                      |                             | Always lift an enemy                         | A4 does not heal                                               |
| Venti              | WIP                 |                                      |                                                      |                             | 8 hits in total                              | A4 may be incorrect                                            |
| Ningguang          |                     | Used if at least 1 Star Jade         | Jade Screen should be correct                        |                             |                                              |                                                                |
| Noelle             |                     | Never used                           | Incomplete                                           |                             |                                              | A1 is incomplete                                               |
| Traveler (Geo)     |                     |                                      |                                                      |                             |                                              |                                                                |
