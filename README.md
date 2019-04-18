# Code Contributions and Review

This is Caxy's code review philosophy.

## Goals

The goals of code review include:

- Reduce the introduction of defects
- Ensure that code meets acceptable quality levels
- Ensure that code adheres to project’s architecture, standards, and best practices
- Share and distribute knowledge
- Facilitate design discussions

See also [Atlassian's nice writeup](https://www.atlassian.com/agile/code-reviews/).

## Process

At a very high level, the code review process should go as follows:

- Author submits code to be reviewed and pings reviewer(s)
- Reviewers review the code and leave feedback for the author
- When the reviewers are satisfied with the changes, they apply the "Approved" label.

In general, the onus is on the author to convince the reviewer that the changes are acceptable. However, the onus is on the reviewer to ensure that the changes requested are reasonable. 

In extremely rare circumstances where the author and reviewer cannot reach consensus, the review can be escalated, however this should be done in only the most extreme circumstances and should never be necessary if both the author and the reviewer are following the advice below.

## As the author

Reviewing code is hard, and as the author of code you should try your best to make the code as easy to review as possible. Here are some tips for doing that:

Read the page on [Writing PRs](https://github.com/dimagi/code-review/blob/es/writing-prs/Writing_PRs.md)

### Responding to feedback

Here are some guidelines for authors responding to feedback during code review.

- Feedback that the author agrees with and is not a major effort should be implemented as part of the code review before the code is merged
- Feedback that the author agrees with and is a major effort can either be done, or discussed and agreed to defer as “out of scope”. The author should make this decision, though the reviewer must agree to it.
- Feedback that the author disagrees with should be discussed until an agreement is reached. 
- Always be respectful when disagreeing, and speak objectively about the code and not about the person.
- If an agreement can’t be reached it can be escalated to senior third party or the team
- After one round of feedback, pair programing should be leveraged to implement changes for the review.

### Scrutinizer (Tin Man)

- scrutinizer-ci.com is a helpful service that will continually monitor Pull Requests and suggests changes to keep code quality, best practices, as well as finding simple bugs.
- As the Author, when opening a Pull Request, Scrutinizer will automatically run, and it's your onus to fix or discuss false positives.

## As the reviewer

The author likely put a lot of work into the code that they wrote. As such it is very important to always be respectful and collaborative in your suggestions and also be very respectful of the author’s time. Here are some tips for reviewers:

- Use the checklist. (In Progress)
- Always keep the focus on the code, not the author
- Always be respectful. Don’t “talk down” to the author or or use any emotional language in discussing code.
- Don’t assume that you have complete context of the change. When in doubt, ask questions before jumping to conclusions.
- When making comments, it’s very helpful to say whether you expect the comment to be addressed before merge (a “blocker”) or not
- For any “blockers” make sure that you communicate (respectfully) why they are blockers (see below).
- All "comments" are to be considered as "blockers" unless otherwise stated.
- If you don’t feel like you have enough context to understand and merge the change, don’t hesitate to ask for an additional reviewer who has more context.
- Utilize scrutinizer and ensure suggestions it makes were completed by the author.

### Blockers

A “blocker” is a change that the reviewer requests be made before the code is merged. A blocker should typically be in one of the following categories:

- An obvious defect
- An obvious improvement that is low effort
- An improvement that is high-effort, but important enough to still be worth doing

In general, and especially in the last scenario, it is important to be very careful and communicate clearly why something is being declared a blocker. Asking your teammates to put in substantial additional work should be viewed as a big deal, and the corresponding benefits of those changes should be easy to articulate and justify the value of the effort being requested.

Many times, items in the second category can be merged and followed up on in future pull requests. This is especially pertinent when the reviewer and reviewee are in different timezones. If the code does not obviously have a defect, the bar to merge should be lower for when reviewing those in a significant timezone difference. It is important though that the feedback does get responded to in a followup PR.
Some practical examples

- Asking the author to write a few simple tests for a change is a reasonable blocker. 
- Asking the author to write tests that would require bootstrapping an entire test framework should not be a blocker unless the code is absolutely mission-critical (and if it is mission-critical code it likely already has a test framework).
- Asking the author to rename a poorly-named function is a reasonable blocker, though could be addressed in a follow up PR
- Using Symfony 4 as an example, using "function indexAction" instead of "function index"a tuple to a namedtuple should likely not be a blocker in a controller would not be blocker.


### Follow-up PR's
- Tickets should be made in the backlog and linked to the PR with the comment in question to ensure a followup will happen.
