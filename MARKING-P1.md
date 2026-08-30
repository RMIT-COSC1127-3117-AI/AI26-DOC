# Marking Guide for AI'26 - Project 1 - Search

This document explains the automarking framework and system used for Project 1 - Search in Pacman.

In the PR of your project repo, you will be provided with:

1. The report from the automarker.
2. A summary of your submission and overall marking, which includes feedback, summaries, submission details, adjustments, development issues, etc.

## TOC

- [Marking Guide for AI'26 - Project 1 - Search](#marking-guide-for-ai26---project-1---search)
  - [TOC](#toc)
  - [Testing set](#testing-set)
      - [Timeout for Q07](#timeout-for-q07)
    - [Testing Q09: Optimised BFS](#testing-q09-optimised-bfs)
    - [Testing Q10](#testing-q10)
      - [UGRD: Iterative Deepening](#ugrd-iterative-deepening)
      - [PGRD: Capsule Problem](#pgrd-capsule-problem)
  - [Raw total/bonus points vs question points](#raw-totalbonus-points-vs-question-points)
  - [Development: Commit Ratio \& Weight](#development-commit-ratio--weight)
  - [Final Mark Result](#final-mark-result)
  - [Challenging your results](#challenging-your-results)
    - [🔍 Before Contacting Us](#-before-contacting-us)

## Testing set

As stated in the project specification, besides the auto-feedback tests we provided to help you develop your solution, we ran a batch of extra tests, as follows:

- `qX`: basic tests for the question, the same ones provided in the feedback autograder (where applicable). This is the minimum expectation: no marks can be obtained if these tests (available to you at all times!) do not pass. 🤝
- `qX-core`: new tests at the same level as the standard `qX` tests, added to check variety and generality of solutions. These are generally worth double the standard `qX` tests, since they are the ones we expect general solutions to pass!
- `qX-goal`: edge cases related to the goal (e.g., start state is the goal, no goal is possible).

There were also some question-specific tests, as follows:

- `q04-eff` and `q04-eff2`: test the efficiency of your A* implementation, complementing the base `q4` test. These check that A* is implemented efficiently enough (e.g., using the correct data structures).
  - `q04-eff`: uses a 4-second timeout (a good but not fully optimised solution takes ~3 seconds).
  - `q04-eff2`: uses a 2-second timeout and gives BONUS marks. An optimised implementation takes ~1.4 seconds: see the Q07 timeout discussion below for the same reasoning applied here. Note this test is worth 0 base points, so anything you score here is pure bonus! 🥪
- `q07-inad`: further tests for inadmissible heuristics.
- `q09*` and `q10*`: tests for the extended questions Q9 and Q10, undergraduate cohort.
- `q09p*` and `q10p*`: tests for the extended questions Q9 and Q10, postgraduate (PGRD) cohort.

#### Timeout for Q07

For this question, we used the following strategy for a more accurate and fair assessment:

- The timeout for Q7 was set to 2 seconds: the time a reasonable solution takes when no heuristic is used (i.e., it returns 0). With a good heuristic, this drops to between 0.2 and 0.8 seconds: 2x to 10x faster! So the timeout is deliberately generous, matching roughly the no-heuristic case. What constitutes a reasonable heuristic was discussed throughout the FAQ.
- Some submissions may time out not because the heuristic is poor, but because the A* implementation itself is inefficient. To separate these two concerns, we ran your heuristic through OUR own efficient A* implementation, so we assess only the quality of the heuristic, not your A* implementation. Your A* implementation is already assessed separately by the `q04-eff` tests (above); it would be unfair for a slow A* to also lower your heuristic's score.
- Everything was benchmarked on the same hardware in a cluster service.

This approach to assessing Q7 improves on standard autograding, as it decouples the quality of the heuristic from the quality of the search algorithm. ✋

### Testing Q09: Optimised BFS

Both PG and UG were asked to produced a modified version of BFS used in Q01-Q04, by either implementing early-goal-checking (UG) or optimised version without duplication of expansions (PG).

In both cases, the solutions should work out-of-the-box when passing a frontier data-structure to the optimised solution provided for Q09. This means that your BrFS (Q02) and UCS (Q03) must work out-of-the box with the new optimised version of BFS provided in Q09. More specifically, will your Q01-Q04 work if the call to `bestFirstSearch` is replaced with the optimised version provided in Q09? If not, you will lose marks for Q09.

### Testing Q10

#### UGRD: Iterative Deepening

This basically follows similar pattern as Q01-Q04 for the search algorithms.

#### PGRD: Capsule Problem

Question 10 for the PGRD (postgraduate) cohort evaluated two components:

1. Correct representation of the problem (state space, actions, goal test, etc.) - worth 5 points.
2. An effective heuristic for the domain - worth 4 points.

For (1), we evaluate your problem representation using OUR UCS algorithm, so you are not penalised if your own search algorithm is buggy or inefficient. 😉 This is assessed by tests `q10p`, `q10p-core`, and `q10p-goal`; the latter two run only if the basic `q10p` test passes first. Test `q10p-goal` checks corner cases like unsolvable tasks (e.g., when all capsules are unreachable or there are no capsules at all!) or trivial cases (e.g., no capsule or food to collect: job done!)

For (2), we run OUR A* implementation with your heuristic in test `q10p-eff`. A blind BFS expands 78,297 nodes to solve this problem in ~8+ seconds. Your heuristic earns points by reducing that expansion count below a series of thresholds: 30,000 nodes for the first point, then 10,000, 4,000, and 500 nodes for one further point each, up to a maximum of 4 points. For reference, our best heuristic expanded only 149 nodes and solved the task in ~0.034 seconds, while a much simpler/basic heuristic expands just 3,682 nodes in ~0.3 seconds still earned 3 points. The total time allowed was 3 seconds, around half of what BrFS would take (to get any benefit out of it!) but much slower than any reasonable heuristic.

## Raw total/bonus points vs question points

The _raw points_ collected for each question contribute to the final points for that question as per the spec. Consider the raw points for Q1:

```plaintext
Question q1: 2/2
Question q1-core: 4/4
Question q1-goal: 2/2
```

Here there are 8 raw points available, but the question is worth 2 points overall (as per spec). So a perfect solution collecting all 8 raw points attracts the full 2 points for Q1. Collecting 4 raw points across those three test cases would attract 1 point for Q1.

> [!NOTE]
> The project as a whole has 69 raw points, contributing to a total of 35 final points as per the spec. The project also includes 3 bonus marks: 2 in `q07` and 1 in `q04-eff`. 😉 That's why you may see up to 72 points out of 69!

## Development: Commit Ratio & Weight

As with P0 ([#63](https://edstem.org/au/courses/29086/discussion/3473008)), your results will also show a commit ratio: the ratio between the number of commits you made and the minimum number of commits expected. A ratio below 1 suggests your development process fell short of expectations. 😢

An HD (80%+) or DI (70%+) submission must not only reach the raw score, but also demonstrate a quality development process and good version-control practice. As explained in P0 and elsewhere, your repo should show evidence of **sustainable, incremental progress towards your solution**, not just the final product. 🙏 A strong AI solution at this level is not only a working system: it also reflects sound, professional development habits.

When the process and commit history are poor (e.g., too few commits, bulk commits, non-atomic commits spanning multiple questions, closed Feedback PRs, incorrect author configuration, or weak commit messages), a multiplier may be applied to the raw points. By default, this weight is equal to the commit ratio when it is below 1; otherwise it is 1 (no effect). It may also be adjusted after manual inspection: for example, an excessive number of trivial commits is also not good development practice. A final weight of 0.75 means only 75% of the raw points are awarded, which also means the submission would no longer be at HD level.

> [!NOTE]
> The expectations around development were stated explicitly in the specification and are fully explained in the [SE-PRACTICES](https://github.com/RMIT-COSC1127-3117-AI/AI26-DOC/blob/main/SE-PRACTICES.md) document, and were also discussed in class and stressed in P0.

This project comprises 10 questions, and many are far from trivial. A full-quality solution should therefore show **at least 13 commits**. This is a deliberately low threshold, representing fewer than 2 commits per question, and many questions clearly warrant significantly more. If a submission achieves full marks with substantially fewer commits, it is likely not showing enough evidence of a solid development process, and the weight may be adjusted. The average HD submission had 23+ commits, with the best solutions reaching 30+. 🥇

> [!Warning]
> Even a full-mark solution with only 13 commits suggests a suboptimal development process: we expect many more. Q7 alone could reasonably take 5+ commits, even for a strong AI programmer. In fact, the average submission had 18+ commits, with the best reaching 30+.

A good development process should be visible in the commit history. For complex questions, we expect multiple commits showing incremental development, bug fixes, optimisations, refactoring, and corrections of mistakes. A single-commit solution that implements everything at once indicates very poor process: at minimum, the questions should be separated into their own commits, and would not qualify as a DI submission.

The expected minimum commit count is **pro rata to the points achieved**. So if you completed half the project, we would not expect all 13 commits. 😉

We also checked that you configured your GitHub author username correctly, did not close the Feedback PR (against instructions), and did not force-push, among other checks.

> [!IMPORTANT]
> The commit count is a PROXY, not a target. The goal is not to hit a “magic” number regardless of how you get there. We look at the actual repository. Ten meaningless commits are just as bad as one bulk commit. The real question is: _looking at the commit history, can one reconstruct the process behind the solution?_ Can we see the incremental development, bug fixes, optimisations, refactoring, and mistakes along the way?
>
> A ratio below 1 indicates fewer commits than expected and suggests that too much work may have been “dumped” into a single commit. 😢

## Final Mark Result

This project is worth 10% of your final grade. We report the outcome of each assessment on the usual 0–100 band so it is clear how you performed relative to the grading bands (pass, credit, distinction, etc.).

The final mark is calculated as follows:

- QUESTION MARK = (RAW QUESTION POINTS / TOTAL QUESTION POINTS) × QUESTION WEIGHT
- FINAL MARK = (SUM(QUESTION MARKS) × WEIGHT) × 100 − LATE PENALTY

WEIGHT defaults to 1 unless a different value is specified (see the Development section above). LATE PENALTY is 0 if the assessment was submitted on time.

## Challenging your results

If, after significant review and analysis on your part, you believe there is a **factual error** in the marking, please post in the Feedback PR of your repo and tag Harry using `@gourdoni`.

> [!CAUTION]
> Do not send emails or post on the forum. 🚫 Only communication in your PR will be considered.

We hope the feedback is clear and detailed. The marking is **(mostly) automated and objective**, based on **unit-testing best practices**, so there is limited room for subjective reconsideration.

- ⚠️ Please do **not** contact teaching staff about this feedback without first reviewing it and your submission carefully. We will not respond to messages that don't demonstrate this has been done beforehand.
- ⚠️ Do **not** ask for "reconsideration" of subjective matters (e.g., *"I think my code is better than what the report says"*). Messages asking for extra marks without justification will not be answered: apologising does not earn marks back. The best way to learn is to understand the feedback and apply it next time.
- ❌ Do **not** send emails or make forum posts about marking: requests made outside this PR will not be processed.
- ⏰ Any challenges or requests must be made **within 5 working days** of receiving this feedback. After that, marks are considered final.

> [!IMPORTANT]
> As discussed in class several times, this course (and university more broadly) is not about judging the final product or effort invested alone. This project exists to help you understand the concepts, foundations, and techniques of AI search: you will ultimately demonstrate your knowledge in the final summative assessment. Thus these projects are more "formative" assessment, and the feedback is here to help you learn towards that final goal. That is also part of why it is worth 10%. 👍

### 🔍 Before Contacting Us

Please carefully review:

- The feedback in this report.
- The marking guide above.
- Your submitted code: the best learning happens when YOU 🫵 find the issue yourself.
