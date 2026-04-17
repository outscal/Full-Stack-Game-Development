**Tasks:**

- Change the name of Enum `**ActionType**` to `**CommandType**`
- Create a struct called `**CommandData**` which stores data relevant for a Unit Command like: `ActorUnitID`, `TargetUnitID`, `ActorPlayerID`, `TargetPlayerID`.
- Refactor `**UnitCommand**` to use the newly created `**CommandData**` struct.
- Remove the method `**IsSuccessful()**` from `**IAction**` interface.
- Update `**PerformAction()**` method to accept another Boolean argument called `**isSuccessful**`.



- Create **concrete commands** for the following unit actions and implement all abstract methods in  `**UnitCommand**` class.
- **Attack**
- **Heal**
- **Cleanse**
- **Attack Stance**
- **Meditate**
- **Berserk Attack**
- **Third Eye**



# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-2-Using-Commands**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-2-Using-Commands**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
