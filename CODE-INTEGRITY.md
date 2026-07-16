## In a code assignment/project, how do I make sure I do not go against academic integrity?

> [!NOTE]
> The examples below refer to Pacman projects done in the AI course, but they generalize to any particular project you may be doing in other courses.

**Good question!** 👏

The simple answer is: your solution has to be **_your_ own intellectual work**. In terms of code, your code **must be written _entirely_ by yourself**. 🫵

* As a rule of thumb, you should never look at or run anyone (human or AI) else's code for the assignment, whether the code was written by someone currently in the class, someone who took it previously, even at another university, or produced by AI tools.

> [!IMPORTANT]
> **Consider this:** everything you are learning in a University course is well-known and done multiple times by thousands of people world-wide. When we ask you to solve problem X or implement algorithm Y, we are not asking you to discover anything new. We are asking you to **_learn_** how to solve it yourself, so you develop your skills and capacity to solve similar problems in the future, in your job. If you look at someone else's solution or get help from AI tools, you are **not learning** how to solve it yourself (besides  **breaching the Course Honesty Policy**), you are merely "watching" 👁️ someone else solve it. It is like going to the gym to watch others lift the weights, you are NOT growing your muscles and you are only cheating yourself in the long run.

- [In a code assignment/project, how do I make sure I do not go against academic integrity?](#in-a-code-assignmentproject-how-do-i-make-sure-i-do-not-go-against-academic-integrity)
- [What to avoid](#what-to-avoid)
- [What you can do](#what-you-can-do)
- [What about AI agents?](#what-about-ai-agents)
- [Final thoughts... 🤔](#final-thoughts-)


## What to avoid

A very smart strategy to protect yourself against breaching the Course Honesty Policy is this one:

🛑 _**Never, ever, _search_ a solution (or part of it) for the project problem you are meant to solve**_. 🛑

* Never search "_A* pacman_" or even "_A* in Python_" or similar, because that is what you need to produce _entirely_ by yourself.
* If you do, you are only tricking yourself, jeopardizing your opportunity to learn, breaching the Course Honor Policy, and putting you at risk of going through the University academic misconduct process.
* In most cases, once you saw someone else's solution or part of it, it is **often too late** for you to come up with YOUR entire solution (which is when you actually learn). It is easy to understand something somebody already solved, the difficult but rewarding task is to build the solution yourself (remember NP problems??)!
* Consider the most important part of a solving process is the start: when you have a blank page and you have to come up with a start yourself. That is when you learn the most, and that is when you are at risk of breaching the Course Honesty Policy if you look at someone else's solution.

**Adapting someone else's (including from AI tools) solution does _not_ make it your own work, no!**. So, if you take, say, an A* implementation (even if not for Pacman) and **adapt** it to your (Pacman) needs, then **the solution is _not_ your own work anymore** and may not be submitted without breaching Academic Integrity. That code is not auxiliary code anymore, it is the code you are meant to produce in your learning journey.

## What you can do

Said so, there are **many things you can do safely** and you are encouraged to! 👍 Let’s discuss them...

1. ✅ **Reading pseudo-code** for a technique, from text-books, papers, the web, or slides, is completely OK and even expected (e.g., reading and studying the pseudo-code for minimax or A* algorithms). If you use a source (e.g., text-book) very closely, for example, converting the pseudocode of A* in the textbook to Python, academic integrity demands that you cite the source (in a comment). You will not be penalized for including such a comment ("_Based on pseudo-code in book X, page Y_”); on the contrary, the citation may help us to understand why your implementation is so similar to someone else's, in case they use and cite the same source.
2. ✅ **Using existing libraries and tools to support auxiliary tasks** that do not involve solving the problem (or an important part of it) we are interested in.

    * For example, **you can use Python libraries for generic tasks** (e.g., math libraries, arrays, etc.); such tasks are not what the project is about and we are not learning how to build those libraries. You can use those libraries off-the-shelf.
    * However, if you find **a library that solves your problem or a non-auxiliarly part of it**, then you **may not use it**. For example, if you find a library of search algorithms, then it is obviously not acceptable to use it, as then you are not solving the problem, you are _reusing someone else's solution_: they won, they know, you don't. :-)

3. ✅ You can also **reuse generic code for specific auxiliary tasks** that you may need, in the path of building your solution to the project problem. For example, if you need to extract the odd numbers you can use:

    ```python
        oddNums = [x for x in nums if x % 2 == 1]
    ```

    or variations of it that are everywhere on the web, as long as you understand what that code is doing. The fact is that that code is auxiliary support code, it does not constitute the core solution to the actual problem you are to solve. So generic Python code is fine to reuse, but remember you need to understand it and unless very trivial _acknowledge it in your code (with a comment)_.

4. ✅ You are **encouraged to discuss with your peers**, even your solutions, but **always at the verbal level**, never sharing or showing code (even snippets), and never seeing step-by-step the code of your friend.

    * It is totally fine to exchange ideas, insights, or tips like: "_why don't you try a dictionary to store X instead of an array?_" or "_remember to check for goal after you extract a node from the open list, not when you expand_" or "_be careful with X, I had a problem when ...._", or "_use library X to do Y, it works much better than Z_", etc.
    * If you just keep the collaboration at the speech level, it is very difficult to do anything wrong; if on the other hand you show or pass code, then you are putting you and your friend into a big risk and missing out in the learning. Don't do it, not worth it.
    * Of course, if it is just about Python, it is OK to go over code, for example it is OK to explain to your friend how you do list comprehension, that is, again, auxiliary code.


Observe you it is totally fine to **research general techniques or techniques for different problems** that you may find useful **importing into Pacman problems**. For example, you may research what is used in pathfinding or in TSP or in network flow problems. Then you may adapt and import those techniques to your specific task. If the problem you researched had nothing to do with Pacman, then you are safe. You will of course, as courtesy and ethical behavior, then explain and acknowledge in your report what you took from where and explain how that was helpful for your solution. For example, in the past, a student reported this which was just perfect:

```
Tried to use the heuristics from question 6. Heuristic was not
acceptable..
......
Realized that ..........
........
Since I now have a fixed the XXXXXXX distance problem, I did some
research online on possible heuristics which may help.
First off, I started with looking up heuristics for problem XYZ since it is
similar.
____________________________________________________________
Solution 1 (commented out in searchAgents.py line 524 - 536)
------------------------------------------------------------

https://abc.cde.fgh.sk/abc-cit/butka/abc.pdf
I adapted the logic behind section 3.1 (ABC XYZ) to see if it
will work. Was able to reduce the nodes expanded to 12372 nodes (2/4)

Solution 2 and 3 were inspired by the behaviour I observed in the the
Corner's problem (Question 6)....
.......
```

As one can see, the student was faced with a problem, as the naive solution did not work well. Then worked out a fix for part of it and then researched techniques in a completely different problem XYZ that the student thought could be imported into Pacman. He adapted it and later did a few changes to make it specific for the Pacman problem at hand. **JUST PERFECT!** :-)

## What about AI agents?

For your best learning, consider AI agents as another "person". If you use it as  **_your_ personal tutor** it should be OK, but not that good tutors never give away answers and their role is to help YOU get to the answers. They are there to help you understand concepts, clarify doubts, and guide you through the learning process,but not as shortcuts to th  answer.

Of course, they should **not** be used to generate complete solutions or code for your assignments, but the should not be used as third entity that give you the answer to problems (even if they are not assessments!), as that will destroy your learning right away. 

What AI Agents COULD do:

- Explain concepts when students are confused, as if they are tutor or the book. For example: "Why does A* use a priority queue instead of a stack or a queue?" is OK.
- Point students to relevant lecture materials or documentation.
- Explain error messages related to programming constructs (e.g., wrong use of tuples or list comprehension) and what they mean.
- Provide small code examples (2-5 lines) to illustrate a specific concept that is NOT the same as the question you are solving but similar. For example: "show me an example of a list comprehension that filters out even numbers from a list of integers" is OK.
- Evaluate a solution or code snippet that you have written in full, and provide feedback on its correctness, efficiency, or style without providing the fixes. 
  - For example: _"have written the following DFS algorithm. Can you check if it is correct? If not, do not tell me how to fix it or exactly where the mistake is, but provide instead some subtle hints, for example what cases could it not work correctly:"_ is OK.


As you can see, the AI agent is there to help you understand concepts, clarify doubts, and guide you through the learning process, but not as a shortcut to the answer. It is what a good tutor would do, and it is what you should expect from a good AI agent. But your prompt needs to guide the AI agent to behave like a tutor, not like a student or contract cheater that gives you the answer. 😉

What AI Agents SHOULD NOT do:

- Write functions or complete implementations.
- Generate full or skeleton solutions to assignments or tutorial questions. Anything that the AI tool produces from scratch is 99% not OK. This is different when YOU gie teh AI tool your solution and you ask it to evaluate and help _you_ improve it.
- Complete TODO sections in assignment code.
- Refactor portions of student code.
- Provide solutions to quiz or exam questions.
- Write more than a few (2-3) lines of code at once (e.g., it is OK if it re-writes a list comprehension statement).
- Convert requirements directly into working code.

>[!CAUTION]
> If in doubt or you are unsure about what is acceptable, please ask the teaching staff. Seeking clarification demonstrates professionalism and academic maturity, and we are always happy to help. 🤝 If you feel too tempted to use AI tools, then it is highly recommended you simply turn it off, if your objective is to learn and be better at the end of the semester. 😉
>
> I personally turn it off around 90% of the time, unless I am doing something that is not related to my core work and does not require intellectual effort. The reasons are two: (1) maintain and improve technical competence; and (2) enjoy the process of building it myself.

## Final thoughts... 🤔

Borrowing from a related [entry from Stackoverflow](http://meta.stackoverflow.com/questions/334822/how-do-i-ask-and-answer-homework-questions) on how to ask questions about assignment, here are some good strategies:

1. **Make a good faith attempt to solve the problem yourself first**. If you can't see enough work on your part, then there is probably a problem.
1. **Ask about specific problems with your existing implementation**. If you can't do that yet because you have nothing, then there is probably a problem.
1. **Admit that the question is homework**. Always be upfront when you ask about assignments (you can structure your question this way: “_How can I do …? I'm trying to do this as part of … which is a homework problem. This is my attempt so far: ..._”).
1. **Never use code you don't understand**. It definitely won't help you later (after school, in later assignments, on tests, etc.) and it could be, at best, very embarrassing if you are asked to explain code you turned in.

Observe that an assignment in a course is **not an open source project** and it is not acceptable to search for help in web forums or to look for solutions that others have made.

**Summarizing:** use help if it is just helping you to come up with the solution by _yourself_. If you do so, at the end you will be proud of _your_ solution. 😉


