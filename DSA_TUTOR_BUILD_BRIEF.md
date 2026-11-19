# Local DSA Tutor — Build Brief

**Purpose:** A portable, implementation-ready brief for building the personal DSA learning app in this or another directory.

**Status:** Core product requirements and proposed technology stack approved in conversation.

## 1. Product summary

Build a local browser app that guides a Java learner from DSA fundamentals through coding-interview readiness. The app—not the AI model—owns the curriculum, lesson order, exercise library, LeetCode assignments, daily plan, progress rules, and statistics. A small local model is a constrained helper that answers learner questions.

### Target learner

- New graduate preparing for full-time software-engineering interviews.
- Knows basic Java; new to data structures and algorithms.
- Wants to start at the beginning and follow one fixed curriculum.
- Chooses how much time is available for each day’s session; no interview countdown is required.

### Product outcome

Help the learner build durable, demonstrable DSA skill: solve unfamiliar problems with progressively fewer hints, explain the approach and complexity, and recall patterns during later mixed practice. Do not promise a job or a guaranteed interview outcome.

## 2. Approved decisions and boundaries

- **Product type:** Personal software first; local-only, single user.
- **Interface:** Browser app running on the learner’s computer.
- **App stack:** React + TypeScript + Vite; small Node.js/TypeScript local service; SQLite.
- **AI runtime:** Ollama with a locally run, quantized 3–4B text model. Keep the model replaceable through configuration.
- **Practice language:** Java. Java is not the app backend language.
- **Java execution:** The local service uses the installed JDK to compile and run only the app’s built-in practice exercises.
- **LeetCode:** Open selected problems on LeetCode; the app tracks progress through explicit user check-ins. Do not scrape, auto-submit, or copy the full problem bank.
- **Curriculum start:** Fixed. Every learner starts at Lesson 1. No placement test, diagnostic-based placement, or skipping ahead.
- **Progression:** Keep the curriculum order fixed. Adaptive mastery means weak topics receive additional drills and scheduled reviews; it does not reorder the course or change the starting point.
- **Voice:** Out of scope for v1; possible upgrade later.
- **Cloud AI, authentication, billing, public deployment, competitive-programming track:** Out of scope for v1.
- **Contest support:** Later enhancement may link to contest pages and let the user set local reminders; do not automate sign-up.

## 3. Curriculum and curated question plan

All lesson explanations, built-in drills, question selection, LeetCode metadata, and hint ladders are curated content. Do not ask the local model to invent or reorder the course. Each LeetCode entry should store only its title, problem ID, URL, difficulty, topic tags, prerequisites, and the app’s own notes/hints—not LeetCode’s full statement or solution.

The sequence below is fixed and is the course’s source of truth. For each topic, teach the built-in drill first, then assign the LeetCode practice in the listed order. Difficulty progression is generally Easy → Medium; advanced items are labeled optional.

### Lesson 1 — Algorithmic thinking and complexity

**Teach:** What an algorithm is; input size; counting work; time versus extra space; O(1), O(n), O(n²), and O(log n) intuition; constraints; brute force before optimization; tracing examples and edge cases.

**Built-in drills:** Count operations in a single loop; compare a single loop with nested loops; identify constant-time array access; state how work changes when input size doubles.

**LeetCode practice:**
- [1920 — Build Array from Permutation](https://leetcode.com/problems/build-array-from-permutation/) — Easy
- [1929 — Concatenation of Array](https://leetcode.com/problems/concatenation-of-array/) — Easy

### Lesson 2 — Arrays, strings, and basic matrices

**Teach:** Indexing, traversal, mutation, in-place updates, string immutability and `StringBuilder`, basic 2D-array coordinates, and subarray versus subsequence.

**Built-in drills:** Find min/max; reverse an array; remove a chosen value in-place; count matching characters; traverse a matrix by row and column.

**LeetCode practice:**
- [1480 — Running Sum of 1d Array](https://leetcode.com/problems/running-sum-of-1d-array/) — Easy
- [27 — Remove Element](https://leetcode.com/problems/remove-element/) — Easy
- [283 — Move Zeroes](https://leetcode.com/problems/move-zeroes/) — Easy
- [121 — Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/) — Easy

### Lesson 3 — Hash maps, sets, and prefix sums

**Teach:** `HashMap`/`HashSet`, frequency counting, membership checks, grouping, prefix sums, and the time/space trade-off of storing information.

**Built-in drills:** Build a frequency map; find the first repeated value; test whether two strings have equal character counts; answer range-sum queries with prefix sums.

**LeetCode practice:**
- [217 — Contains Duplicate](https://leetcode.com/problems/contains-duplicate/) — Easy
- [1 — Two Sum](https://leetcode.com/problems/two-sum/) — Easy
- [242 — Valid Anagram](https://leetcode.com/problems/valid-anagram/) — Easy
- [49 — Group Anagrams](https://leetcode.com/problems/group-anagrams/) — Medium
- [238 — Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/) — Medium
- [560 — Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/) — Medium

### Lesson 4 — Two pointers and sliding windows

**Teach:** Pointer invariants; inward and same-direction pointers; fixed and variable windows; when a sorted input enables a pointer strategy.

**Built-in drills:** Check a palindrome; find a target pair in a sorted array; move a window while maintaining a sum; track the longest window satisfying a simple condition.

**LeetCode practice:**
- [125 — Valid Palindrome](https://leetcode.com/problems/valid-palindrome/) — Easy
- [167 — Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/) — Medium
- [11 — Container With Most Water](https://leetcode.com/problems/container-with-most-water/) — Medium
- [15 — 3Sum](https://leetcode.com/problems/3sum/) — Medium
- [209 — Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/) — Medium
- [3 — Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/) — Medium

### Lesson 5 — Sorting, binary search, and intervals

**Teach:** Java sorting and comparators; why sorting helps; binary-search invariants and boundaries; first/last occurrence; rotated arrays; merge/sweep interval reasoning.

**Built-in drills:** Implement lower-bound search; test empty/singleton arrays; merge two sorted ranges; sort intervals and identify overlaps.

**LeetCode practice:**
- [704 — Binary Search](https://leetcode.com/problems/binary-search/) — Easy
- [35 — Search Insert Position](https://leetcode.com/problems/search-insert-position/) — Easy
- [34 — Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/) — Medium
- [33 — Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/) — Medium
- [56 — Merge Intervals](https://leetcode.com/problems/merge-intervals/) — Medium
- [57 — Insert Interval](https://leetcode.com/problems/insert-interval/) — Medium

### Lesson 6 — Linked lists, stacks, and queues

**Teach:** References and pointer rewiring; sentinel/dummy nodes; fast/slow pointers; LIFO/FIFO; `ArrayDeque`; monotonic stack only after ordinary stack use is understood.

**Built-in drills:** Reverse a linked list; find its midpoint; detect a cycle; validate balanced delimiters; implement a queue using two stacks; find next-greater values with a monotonic stack.

**LeetCode practice:**
- [206 — Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/) — Easy
- [21 — Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/) — Easy
- [141 — Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/) — Easy
- [876 — Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/) — Easy
- [20 — Valid Parentheses](https://leetcode.com/problems/valid-parentheses/) — Easy
- [155 — Min Stack](https://leetcode.com/problems/min-stack/) — Medium
- [739 — Daily Temperatures](https://leetcode.com/problems/daily-temperatures/) — Medium

### Lesson 7 — Recursion and divide-and-conquer

**Teach:** Call stack, base case, recursive contract, shrinking input, recurrence intuition, and how merge sort divides and combines work.

**Built-in drills:** Trace a recursive call tree; sum a range recursively; reverse a string recursively; merge two sorted halves.

**LeetCode practice:**
- [509 — Fibonacci Number](https://leetcode.com/problems/fibonacci-number/) — Easy; first solve directly, then revisit in DP
- [50 — Pow(x, n)](https://leetcode.com/problems/powx-n/) — Medium
- [24 — Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/) — Medium

### Lesson 8 — Trees and binary search trees

**Teach:** Tree vocabulary; recursive DFS traversals; BFS/level order using a queue; subtree results; paths; BST ordering invariant and lowest common ancestor.

**Built-in drills:** Write preorder/inorder/postorder; compute depth; return a property from children; validate a BST; traverse a tree level by level.

**LeetCode practice:**
- [104 — Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/) — Easy
- [226 — Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/) — Easy
- [543 — Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/) — Easy
- [102 — Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/) — Medium
- [98 — Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/) — Medium
- [236 — Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/) — Medium

### Lesson 9 — Heaps and priority queues

**Teach:** Min-heap/max-heap behavior; Java `PriorityQueue`; top-K; repeated min/max; merging sorted streams; when a heap is better than sorting everything.

**Built-in drills:** Keep the k largest values seen; merge sorted lists by repeatedly selecting the smallest head; maintain two heaps for a running median (advanced).

**LeetCode practice:**
- [215 — Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/) — Medium
- [347 — Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/) — Medium
- [973 — K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/) — Medium
- [23 — Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/) — Hard
- [295 — Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/) — Hard; optional

### Lesson 10 — Backtracking

**Teach:** Choose/explore/undo; decision trees; base cases; duplicate handling; pruning; distinguish enumerating possibilities from optimizing over overlapping subproblems.

**Built-in drills:** Generate subsets; generate permutations; choose combinations summing to a target; search a small word grid.

**LeetCode practice:**
- [78 — Subsets](https://leetcode.com/problems/subsets/) — Medium
- [46 — Permutations](https://leetcode.com/problems/permutations/) — Medium
- [39 — Combination Sum](https://leetcode.com/problems/combination-sum/) — Medium
- [17 — Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/) — Medium
- [79 — Word Search](https://leetcode.com/problems/word-search/) — Medium

### Lesson 11 — Grids and graphs

**Teach:** Model nodes and edges; adjacency list; directed/undirected and weighted/unweighted graphs; visited sets; grid BFS/DFS; components and cycles; topological order; union-find; unweighted shortest paths; Dijkstra after heaps.

**Built-in drills:** Flood-fill a grid; count connected components; find a shortest path in an unweighted grid; detect a dependency cycle; implement union-find operations.

**LeetCode practice:**
- [733 — Flood Fill](https://leetcode.com/problems/flood-fill/) — Easy
- [200 — Number of Islands](https://leetcode.com/problems/number-of-islands/) — Medium
- [994 — Rotting Oranges](https://leetcode.com/problems/rotting-oranges/) — Medium
- [133 — Clone Graph](https://leetcode.com/problems/clone-graph/) — Medium
- [207 — Course Schedule](https://leetcode.com/problems/course-schedule/) — Medium
- [684 — Redundant Connection](https://leetcode.com/problems/redundant-connection/) — Medium; union-find
- [743 — Network Delay Time](https://leetcode.com/problems/network-delay-time/) — Medium; Dijkstra
- [127 — Word Ladder](https://leetcode.com/problems/word-ladder/) — Hard; optional

### Lesson 12 — Greedy algorithms

**Teach:** Local choices, counterexamples, exchange/ordering intuition, and explaining why a choice is safe. Reuse sorting and intervals rather than treating greedy as a memorized template.

**Built-in drills:** Select the maximum number of non-overlapping activities; choose interval order; test a tempting greedy rule against a counterexample.

**LeetCode practice:**
- [55 — Jump Game](https://leetcode.com/problems/jump-game/) — Medium
- [435 — Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/) — Medium
- [452 — Minimum Number of Arrows to Burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/) — Medium
- [134 — Gas Station](https://leetcode.com/problems/gas-station/) — Medium
- [621 — Task Scheduler](https://leetcode.com/problems/task-scheduler/) — Medium

### Lesson 13 — Dynamic programming

**Teach:** Recognize overlapping subproblems; define state in words; derive transition and base cases; start with recursion, add memoization, then tabulate; 1D, grid/2D, knapsack/subset, and subsequence/string patterns.

**Built-in drills:** Re-solve Fibonacci with memoization and tabulation; define `dp[i]` before coding; fill a small grid table by hand; explain why a state transition covers all cases.

**LeetCode practice:**
- [70 — Climbing Stairs](https://leetcode.com/problems/climbing-stairs/) — Easy
- [198 — House Robber](https://leetcode.com/problems/house-robber/) — Medium
- [62 — Unique Paths](https://leetcode.com/problems/unique-paths/) — Medium
- [322 — Coin Change](https://leetcode.com/problems/coin-change/) — Medium
- [416 — Partition Equal Subset Sum](https://leetcode.com/problems/partition-equal-subset-sum/) — Medium
- [300 — Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/) — Medium
- [1143 — Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/) — Medium
- [72 — Edit Distance](https://leetcode.com/problems/edit-distance/) — Hard; optional

### Lesson 14 — Mixed interview practice and advanced extensions

**Teach:** Topic labels hidden; clarify, derive brute force, optimize, explain, code, test, analyze. Revisit old questions and solve new variations. Add optional extensions only after core review: tries, bit manipulation, advanced graph algorithms/MST, segment/Fenwick trees, advanced DP, and specialized string algorithms.

**Mixed practice:** Reassign previously curated problems without topic labels; add original variants to avoid measuring memorization of known answers.

## 4. Daily plan and mastery behavior

The learner enters available minutes for today. Scheduling is deterministic and does not use an interview date or ask the model to choose work:

1. Schedule due review items first.
2. Continue at the next item in the fixed curriculum order.
3. Fit a lesson/drill/problem into the remaining budget; if the session is too short for a new concept, offer review instead.
4. After an unsuccessful attempt, add targeted practice/review. Do not mark a lesson secure merely because its page was opened.

Track at minimum: lesson and exercise completion, problem attempts, self-reported LeetCode outcome, time spent, hint level, review due date, and mastery state (`new`, `learning`, `review`, `secure`). A topic is secure only after independent evidence such as solving a new representative exercise, explaining the approach/complexity, and succeeding on a later recall attempt. Keep progress visible and correctable by the user.

## 5. Local AI helper boundaries

The model is a small, local text assistant—not the curriculum engine or judge.

**Allowed:** Answer a learner’s question about the current lesson; explain a term or code line; give a hint when requested; discuss learner-pasted custom problem text/code; clarify why a local exercise test failed.

**Not responsible for:** Creating or reordering lessons; selecting the daily plan; inventing official LeetCode content; deciding completion/mastery; claiming code is correct without running tests; submitting code to LeetCode; contest registration; sending prompts/code to a cloud service.

Provide the assistant with relevant curated lesson notes, problem metadata, and learner-provided context. Keep its chat panel optional; the app must remain useful if Ollama is stopped or the model gives a poor answer. Show a clear local-model unavailable/error state. No voice in v1.

## 6. V1 product areas

1. **Today:** available-time input, today’s plan, due reviews, quick progress summary.
2. **Curriculum:** fixed ordered lessons and status; Lesson 1 is the only starting point.
3. **Practice:** built-in Java exercises with editor, run button, visible test results, and optional hint ladder.
4. **LeetCode list:** curated problem assignments with external links and manual result/time/hint logging.
5. **Ask the tutor:** local chat for lesson or user-selected problem doubts.
6. **Progress:** solved independently, solved with hints, attempts, time, topic mastery, and due reviews.
7. **Custom question:** paste a question and optionally code, then ask the local helper. Do not auto-generate an assignment from it.

## 7. Proposed local architecture

- **Frontend:** React + TypeScript + Vite; desktop-first responsive browser UI.
- **Local service:** Node.js + TypeScript API. Owns SQLite persistence, daily-plan rules, exercise compilation/execution, and the Ollama adapter.
- **Persistence:** SQLite database stored in the app’s local data directory. No account or remote sync.
- **Inference:** Ollama local API. Start with one quantized 3–4B text model; make model name and endpoint configurable. Do not require a cloud fallback.
- **Java runner:** Use an installed JDK to compile/run only the app’s built-in exercises in temporary workspaces. Enforce timeouts, bounded output, cleanup, and safe error reporting. Do not execute arbitrary shell commands from model output.
- **LeetCode workflow:** Open the official URL externally; the user manually records result and time. No scraping or browser automation.
- **No microservices:** This is one local application with clear modules; do not add cloud infrastructure, queues, caching, or external analytics.

## 8. Implementation order

1. **Curriculum and static catalog:** Encode the fixed lesson order, original drill metadata, selected LeetCode IDs/URLs, difficulties, prerequisites, and authored hint ladders. Validate every link and ensure no full third-party statement/solution is copied.
2. **Local app shell and persistence:** Render the ordered curriculum and store local user progress in SQLite.
3. **Java exercise runner:** Implement built-in exercises, compile/run results, timeouts, and clear diagnostics. Test this independently before connecting it to lesson UI.
4. **Daily planner and review rules:** Accept any daily time budget; schedule due review and the next sequential task; verify no diagnostic or skip path exists.
5. **Progress and LeetCode logging:** Record local exercise results and manual external problem outcomes; show meaningful stats.
6. **Ollama doubt helper:** Add scoped lesson/problem context and error states. Verify the rest of the app works offline without a loaded model.
7. **Personal validation:** Use it for at least 10 real sessions; evaluate tutoring usefulness, time-budget fit, Java exercise reliability, and whether review brings back weak topics.

## 9. Acceptance criteria

- A fresh install always opens at Lesson 1; there is no placement test or skip-ahead control.
- Lesson and LeetCode assignment order matches this document.
- User can enter daily available minutes and receive a plan that respects the fixed order and due reviews.
- Built-in Java exercises compile/run locally and show pass/fail output, compiler errors, and timeouts without crashing the app.
- Each LeetCode link opens the selected official problem; attempts and solve status are recorded only after user check-in.
- Stats distinguish independent solves from solves with hints and external LeetCode check-ins.
- Topic weakness causes additional practice/review, not a curriculum reorder.
- The tutor answers only when invoked and does not change lessons, plans, progress, or completion status.
- Model stopped/unavailable does not prevent access to curriculum, exercises, or saved progress.
- User progress and chat are stored locally; no login, cloud sync, telemetry, or silent cloud model calls.

## 10. Risks and implementation notes

- A 3–4B model may give incorrect algorithmic explanations. Keep it grounded in curated material; exercise tests and authored content remain authoritative.
- The user’s laptop has 16 GB RAM and an RTX 3050 Laptop GPU with 4 GB VRAM. Keep the model configurable, use a modest context, and report latency/model-load failures clearly.
- Java execution is a local code-execution surface. Keep the runner narrow, process-limited, isolated to temporary exercise files, and independent of model-generated shell commands.
- LeetCode problem text and solutions are third-party content. Store IDs/links and original study notes; do not mirror the platform’s full content.
- “Mastery” is evidence-based but not a guarantee of interview or job success. Make the state explainable and user-correctable.

## 11. Research basis for the curriculum

The topic set and order synthesize public curricula and learner reports. The precise ordering is our learner-first recommendation; sources do not agree on one canonical order. Social posts are anecdotal and may be promotional, so use them as learner signals rather than proof of topic frequency.

- [NeetCode — DSA for Beginners](https://neetcode.io/courses/dsa-for-beginners/0): beginner-focused, deliberately sequenced core topics.
- [NeetCode — How to Prepare for Coding Interviews](https://blog.neetcode.io/p/prepare-coding-interviews): patterns, repetition, and review rather than random volume.
- [Tech Interview Handbook — Algorithms Study Cheatsheet](https://www.techinterviewhandbook.org/algorithms/study-cheatsheet/): interview topic priority and practical preparation notes.
- [LeetCode — Interview Crash Course](https://leetcode.com/explore/featured/card/leetcodes-interview-crash-course-data-structures-and-algorithms): official interview-focused topic coverage and worked examples.
- [Reddit — DSA learning order](https://www.reddit.com/r/leetcode/comments/1pnf4hs/dsa_learning_order/): learner discussion noting no universally best order and the importance of prerequisites.
- [Reddit — Complete beginner in DSA with Java](https://www.reddit.com/r/leetcode/comments/1rdn66k/complete_beginner_in_dsa_with_java_fully): beginner-specific Java study discussion.
- [LinkedIn — 75-day DSA roadmap](https://www.linkedin.com/posts/anjali-viramgama_75-day-dsa-roadmap-activity-7473756354109837312-3rXY): creator roadmap emphasizing patterns, review, and explaining reasoning.
- [ACM — Spaced, interleaved retrieval practice in introductory programming](https://dl.acm.org/doi/10.1145/3291279.3339411): evidence informing topic review and spaced recall.
