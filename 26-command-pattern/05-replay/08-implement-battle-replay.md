**Tasks:**

- Add a replay button in Game End UI
- Create a new `**GameEventController**` in `**EventService**` for starting replaying a battle.
- Invoke this event when the replay button is clicked.
- This event should:

1. Set Replay State as Active
2. Set Input State as Inactive
3. Game End UI should be disabled
4. Battle Service should reload the the recently played battle.
5. Command Invoker should set the replay stack inside Replay Service.



# Submission Instructions:


---



1. Commit and Push all your changes in the feature branch → *[*`**Feature-4-Replay**`*]*
2. Don't try to commit or merge your changes in the parent repo (the one you forked from) The Parent repo is also called the upstream repo.
3. So avoid pushing or merging commits in any upstream branches.
4. Once you are done with pushing all your commits for this assignment, create a PR from the `**Feature-4-Replay**` branch to the `**main**`
5. Submit the link of this PR as the submission link for this assignment.
