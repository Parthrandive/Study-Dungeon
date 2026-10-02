Study Dungeon: MVP Plan

One-liner: An AI dungeon that teaches you any syllabus topic and rebuilds itself around what you keep failing.
Track: Best Apps and Agents (+ Best Use of Tavily). Deadline: Oct 30, 10:00am PDT (about 10:30pm IST). Aim to submit Oct 28.

1. Core Assumption

Students will use a game to learn a topic from scratch, and come back for the next unit. If they play once and leave, it's a novelty and not a product.

2. Minimum Feature Set
Input: a topic name or pasted syllabus
Agent splits it into 5 concepts (the dungeon map)
Learn room: short lesson + example, grounded in Tavily sources, with the source links shown
Boss fight: 3 questions per concept (MCQ + short answer), HP, win/lose
Weak-spot memory: failed concepts return as harder bosses in the next dungeon
Study pack: PDF export (lessons, your mistakes, revision sheet)
Shareable result card
3. What Gets Cut

Accounts, leaderboards, multiplayer, voice, generated art, payments, mobile app, DOCX export, PDF/notes upload (plain text paste only), numeric and code-answer grading.

4. Architecture
Topic/syllabus → Ultra: concepts → Tavily: sources → Ultra: lesson + questions
→ Game (HP, levels) → Nano: hints/feedback, Ultra: grading → memory → study pack
Part	Choice
Frontend	React/Next.js (your strength)
Backend	Small FastAPI service
Models	Nemotron Ultra for planning and grading, Nano for hints and quick calls (via Token Factory)
Search	Tavily
Budget savers	Cache lessons by topic, generate level 1 first and the rest while they play
Privacy	Memory stored per browser session, no accounts
5. Test Criteria (behavioral)
40+ students start a dungeon
50%+ finish a unit
30%+ start a second unit within 7 days
10+ export a study pack or share a result card

Under 15% returning means the core assumption is wrong.

6. Timeline
Day (date)	Do
1–2 (Oct 2–3)	Repo (MIT license), dungeon JSON schema, hardcoded dungeon, game loop with HP and win/lose. No API needed while credits arrive
3 (Oct 4)	Token Factory first call, concept-splitting prompt
4	Tavily search + lesson/question generation
5	Answer grading
6	Weak-spot memory
7	Study pack export + deploy
8	10 friends play. Watch where they get stuck
9–10	Fix grading errors and the top 3 problems
11–12 (Oct 12–13)	Launch to college groups and LinkedIn
13	Measure
14 (Oct 15)	Decide
15–26	Iterate on feedback, record the 3-min video, write the README and Nebius feedback
27–28 (Oct 28)	Submit
7. Top Risks
Risk	Handling
Unfair grading drives users away	MCQ first, short answers graded against a reference answer from sources
Slow generation	Stream level 1 first
Web content is wrong	Show source links on every lesson
Looks like "ChatGPT in a game skin"	Weak-spot memory and the study pack are the product, so lead with them in the demo
Credits run out	Cache, and use Nano wherever possible