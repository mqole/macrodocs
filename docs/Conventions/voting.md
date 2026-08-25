---
tags:
  - conventions
---

# Voting

Macrocosm utilizes consensus decision-making, where any contributor may create a pull request, and each Microcosm must vote on that pull request before it is merged.

All pull requests fall under one of four categories:

* Category A: Universally Desired
* Category B: Universally Agreed-on
* Category C: Extreme Maintenance Burden
* Category D: Intended Behavior
* Category E: Upstream Merge (colloquially "upmerge")

The categorization of each Pull Request is done by the triage team.

### Category A: Universally Desired

This is a pull request where all Microcosms agree that they want this content and are happy to have it in their codebase. 

Category A pull requests require unanimous agreement, **with no abstains or blocking votes**. Blocking votes are expected to have a written explanation behind the block, ideally with suggested course of action on what would be needed to change their vote.

Even if a pull request is under Category A, the policy regarding customization still applies: there should always be a simple way to disable the content.

### Category B: Universally Agreed-on

This is a pull request where all Microcosms are fine if not completely enthusiastic with the content. This is also where pull requests regarding altering a Wizard's Den upstream merge will land.

Category B pull requests require agreement **with no blocking votes**; abstentions are allowed. Blocking votes are expected to have a written explanation behind the block, ideally with suggested course of action on what would be needed to change their vote.

### Category C: Extreme Maintenance Burden

This is a pull request that represents the collaborative effort between multiple Microcosms on a project that is better handled on the shared platform rather than in their respective downstreams. Potential examples of a Category C pull request would be a mechanically complex major antagonist, a complete UI rework, or other large-scale gameplay overhaul.

Category C pull requests require agreement **with no blocking votes**; abstentions are allowed. Category C pull requests will receive the highest scrutiny out of anything as they represent the largest risk to the overall stability of the project.

### Category D: Intended Behavior

This is a pull request that fixes an unintended issue with a feature to bring it closer to its original design intent. These pull requests are considered "pre-approved", as the feature's correct design intent has already been voted on and approved in the past. Because of this, Category D pull requests can only change features added by Macrocosm.

Category D pull requests **do not require a vote**, only a passing code review, but any Microcosm representative may flag the pull request to be retriaged to a different category, even if they are not a code reviewer or a member of the triage team.

Category D does **not** apply to "subjective" changes, such as balance tweaks, unless the original value in question is blatantly contradictory to the intended design. 

- ***Applicable:*** The metabolism delay of a species is meant to be `0.5x` as long, but was written as `2x` instead.
- ***Not Applicable:*** The metabolism delay of a species is `2x` as long, but a contributor thinks this is too much and wants to make it `1.5x` instead. This would likely be Category A.

### Category E: Upstream Merge

This is a pull request that exclusively pulls changes from Wizard's Den's `master` branch. A single category E pull request may contain dozens of features, each represented by its own commit within the pull request. For this reason and in order to maintain organisation of the codebase, upstream merges **must be merged via a merge commit** as opposed to squash merging.

Like category D, these pull requests are considered "pre-approved", and **do not require a vote** as it is expected that Wizard's Den will have provided a level of quality control as to the pull request's contents.

If the author of a category E pull request suspects that commit(s) within the pull request may require a vote, they should make note of these commit(s) within the body of the pull request. All category E pull requests require **at least one triage review** to catch any commit(s) that may require a vote. Any Microcosm representative may initiate a vote to revert any commit(s) within this pull request at their discretion. If such a vote passes, reverting the commit(s) should be done in a seperate pull request.

Any "fix commits," or otherwise any commits that do not belong to Wizard's Den, must be rebased using `git rebase -i` to keep the number of commits to a minimum. These commits require **at least one code review** before the pull request may be merged.

:::note

Expect more detailed documentation on the technical aspects of how to properly perform an upmerge in the future.

:::

Category E pull requests require the following documentation:
- Any merge conflicts that were resolved between Macrocosm and Wizard's Den, and how they were resolved.
- Any changes made to Macrocosm content that could be classified as a 'breaking change' by the standards of other pull request categories (for example, replacing one component with another after an upstream refactor).
- Any changes that were made to resolve test fails if such a change was not already documented by the above criteria.