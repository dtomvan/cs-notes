---
  pageDecoration:
    icon: book-open
  tags: course
---

# Discrete structures

- Ocasys: https://ocasys.rug.nl/current/catalog/course/WBCS011-05#WBCS011-05.2026-2027.1
- Book: https://u.toostveen.nl/dms and https://discrete.openmathbooks.org
- Lectures: Wednesday (4h!)
- Tutorials: Tuesday
- Assessment: final (90%), quizzes/homework (10%), _no midterm_
  - The idea is that hw is worth nothing so you don’t have to use ChatGPT to pass and the assignments are mostly for your own sake
- Lecturer: Ivan Blitznets

---

Weekly notes:

<!--#lua 
query[[
  from p = index.contentPages()
  where string.startsWith(p.ref, editor.getCurrentPage() .. "/")
  select templates.pageItem(p)
]]
 -->
* [[Courses/Year 1/Semester 1b/Discrete Structures/Week 1]]
* [[Courses/Year 1/Semester 1b/Discrete Structures/Week 2]]
<!--/lua-->

PDFs:

<!--#lua 
query [[
  from p = index.documents()
  where string.startsWith(p.name, editor.getCurrentPage()) and p.contentType == "application/pdf"
  select templates.pageItem(p)
]]
 -->
* [[Courses/Year 1/Semester 1b/Discrete Structures/L0.pdf]]
* [[Courses/Year 1/Semester 1b/Discrete Structures/L1-2.pdf]]
<!--/lua-->