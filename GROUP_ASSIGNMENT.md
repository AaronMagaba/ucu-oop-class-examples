# Group assignment: extend your story together

**Due: Thursday, 15 October 2026.**

Work with your existing group on one story. Your group will use its own fork of this repository. A fork is your group's copy on GitHub. A branch is one member's working version inside that copy. A pull request, or PR, asks the group to review a branch before adding its changes to `main`.

The final `main` branch must contain working contributions and a merged PR from **every member**.

## 1. Choose one extension per person

Open `EXTENSIONS.md` inside your story folder. Each story has six extensions.

- A group of five chooses any five different extensions.
- A group of six completes all six extensions.
- Each person is responsible for one extension, their own branch, their own commits and their own PR.
- Everyone also reviews every other member's PR and leaves a useful comment.

Make a simple list of members and their tasks before coding. Help each other, but each member must write, check and explain their own contribution.

## 2. Make one fork for the group

Choose one member to own the group's fork. That member signs in to GitHub, opens [the class repository](https://github.com/slubambo/ucu-oop-class-examples), and clicks **Fork**. Create the fork under that member's account.

All members use **this same group fork**. You do not need five or six separate forks. Keep the default branch name `main`.

If your group already made a fork before this assignment was added, use **Sync fork** on its GitHub page to bring in the latest instructions before starting. If GitHub reports a conflict, ask for help rather than discarding the group's work.

## 3. Give every member access

The fork owner opens the **group fork**, then **Settings → Collaborators → Add people**. Invite all the other members by their GitHub usernames. Each person must accept the invitation. The owner already has access and does not need to invite themselves.

Each member needs their own GitHub account. Do not all commit or review using the owner's account: the contribution and review must show who did the work. GitHub's [collaborator guide](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/repository-access-and-collaboration/inviting-collaborators-to-a-personal-repository) explains these steps.

## 4. Download the group fork and create your own branch

Clone the **group fork**, not the lecturer's repository. On its GitHub page, open **Code**, copy its HTTPS URL, and use that URL with `git clone`.

For example, replace `GROUP-OWNER` and `GROUP-REPO` with the account and repository name shown on your group's GitHub page:

```sh
git clone https://github.com/GROUP-OWNER/GROUP-REPO.git
cd GROUP-REPO
git switch main
git pull origin main
git switch -c amina-26b12345
```

Use a short branch name containing **your first name and university access number**. `amina-26b12345` is a made-up example. Replace it with your own details, use lower-case letters, and replace spaces or slashes with hyphens.

Each member creates a different branch. Code on your personal branch; changes reach `main` through a reviewed PR.

If you use GitHub Desktop, clone the group fork, fetch the latest `main`, and choose **New branch** with your personal branch name. The same assignment rules apply.

## 5. Write your extension and show that it works

Read your story's `EXTENSIONS.md`. Add the feature to that story's `story.py` and create your own small demo file beside it. Leave the original `main()` and `expected_output.txt` as the baseline story. Your demo should show the new feature separately.

Run the original story and your demo. Show a normal case and a refused, empty or boundary case. If the feature only reads information, show that it leaves the stored resource and history unchanged.

Commit your work using your own Git identity. Make sure Git is configured with your name and an email linked to your GitHub account, or your GitHub-provided private email. This helps GitHub show the contribution under the correct member.

For example, replace the branch, story folder and demo file with yours:

```sh
git add stories/01_rolex_rescue/story.py stories/01_rolex_rescue/demo_amina_26b12345.py
git commit -m "Add lunch wallet top-up and demo"
git push -u origin amina-26b12345
```

In GitHub Desktop, review the changed files, write a clear commit message, commit to your personal branch, then publish or push that branch.

## 6. Open a PR into your group's main branch

On the **group fork**, open **Pull requests → New pull request**. Check the destination before creating it:

| Field | Choose |
|---|---|
| Base repository | Your group's fork |
| Base branch | `main` |
| Head/compare repository | Your group's fork |
| Compare branch | Your personal branch |

A fork can suggest the lecturer's repository as the destination. For this assignment, change the base repository to **your group's fork**. All members' work must come together in the group's `main` branch. GitHub's [PR guide](https://docs.github.com/en/pull-requests/how-tos/create-pull-requests/creating-a-pull-request-from-a-fork) explains the base and compare fields.

Use a clear title, such as `Extension 2: lunch wallet top-up — Amina`.

In the PR description, write:

- Your name, access number and extension number.
- What you added and where it is in the code.
- How to run your demo.
- The inputs, expected results and actual results for your checks.

Each member must author their own PR. Ask all the other members to review it.

## 7. Everyone reviews and comments before merge

For **each PR**, every other group member must:

1. Open **Files changed** and read the code.
2. Run the proposed change, or go through its demo with the author and check the results.
3. Leave at least one useful comment on that PR. Name a method, a rule or a case you checked. Explain what works or what should change.
4. If you started a pending review, **submit it** so the author can see the comment.

Examples of useful comments:

> I tried a top-up of zero. The method returned False and the balance stayed the same. This matches the rule.

> This method should refuse a negative amount before changing the balance. Please add that check and show the result in the demo.

“Good”, “done” or an emoji alone is not enough. The author responds to questions and fixes problems on the **same branch**. Pushing more commits updates the same PR; there is no need to open a replacement PR for each fix.

For a five-person group, each PR needs comments from its **four teammates**. For a six-person group, each PR needs comments from its **five teammates**. The author checks their own work and responds, but does not count as a teammate reviewer on their own PR. GitHub also does not allow authors to approve their own PRs. See [GitHub's review guide](https://docs.github.com/en/pull-requests/how-tos/review-pull-requests/reviewing-proposed-changes-in-a-pull-request).

Everyone therefore reviews all the other members' PRs. If a new commit changes a part you reviewed, check that change again before the PR is merged.

## 8. Bring in the latest group work and merge

Merge PRs **one at a time**, after all teammate comments are present and requested fixes are complete. A member with access can perform the merge; the PR must still be authored by the person who did that extension.

Before merging your PR, bring the group's latest `main` into your branch and run the original story and **all available member demos** again. On your personal branch:

```sh
git fetch origin
git merge origin/main
```

If Git reports a conflict, the group has changed the same lines in different branches. Work with the other author, keep both intended features, remove the conflict markers and run the code again. Stage the resolved files and complete the merge commit as Git instructs, then push your branch. Do not replace the file with only your own version and lose another person's extension.

Once the code works and the review is complete, use **Merge pull request → Create a merge commit → Confirm merge**. Use the merge-commit option for this assignment so the group history clearly keeps each member's work and its PR.

After a PR is merged, each member updates their own local `main`:

```sh
git switch main
git pull origin main
```

If you still have uncommitted work on your personal branch, commit it there before switching. To continue your extension, switch back to your personal branch and bring in the latest `origin/main` before making more edits.

## 9. Record the group's work

Copy [GROUP_TEMPLATE.md](GROUP_TEMPLATE.md) to a file called `GROUP.md` in the root of the group fork. Fill in your group number, story, members, extension numbers, branch names and PR links. One member can create the first version in their own PR; the others can update their rows in their own PRs. Agree on this before editing the same file.

Keep only five member rows for a five-person group, or all six for a six-person group. Use the actual merged PR links, not only branch links.

## 10. Submit your group work

Submit **one link to the group fork** through the normal class submission channel by **Thursday, 15 October 2026**. `GROUP.md` should make it easy to find all members and their merged PRs. Each member should know the submission link and be able to explain their own feature.

Before submitting, check the final `main` branch:

- [ ] All five chosen extensions work for a five-person group, or all six for a six-person group.
- [ ] Every member has a working extension, their own commits and their own merged PR.
- [ ] Each PR has useful comments from every other member, made before merge.
- [ ] The original story still runs and matches its original expected output.
- [ ] Every member's demo runs from the final `main` branch.
- [ ] No merge conflict markers remain in the files.
- [ ] `GROUP.md` lists all members, their extensions, branches and merged PR links.

A PR that is still open, a branch that was never merged, or code copied into `main` without the member's PR does not meet the contribution requirement. The submitted group fork is the final place to look for the completed work.
