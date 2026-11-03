---
pageDecoration: 
  icon: book-open
tags: course
---
# Intro to logic

- Ocasys: https://ocasys.rug.nl/current/catalog/course/WBCS030-05
- Book: https://u.toostveen.nl/lpl
- Lectures: Mon 17-19, Tue 11-13 every week
- Tutorials: Wed/Thu
- Assessment: 2 HW, MT, Exam
- Textbook: LPL + syllabus
- Software: FitchVIZIER https://fitch.rug.themisjudge.nl/

---
- [[Courses/Year 1/Semester 1a/Introduction to Logic/Q&A]]
- [[Courses/Year 1/Semester 1a/Introduction to Logic/Summary|Summary]]

Weekly notes:
<!--#lua query[[
  from p = index.contentPages("week")
  where p.parentCourse == "[[" .. editor.getCurrentPage() .. "]]"
  select templates.pageItem(p)
]] -->
* [[Courses/Year 1/Semester 1a/Introduction to Logic/Week 1]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/Week 2]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/Week 3]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/Week 4]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/Week 5]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/Week 6]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/Week 7]]
<!--/lua-->

PDFs:

<!--#lua query [[
  from p = index.documents()
  where string.startsWith(p.name, editor.getCurrentPage()) and p.contentType == "application/pdf"
  select templates.pageItem(p)
]] -->
* [[Courses/Year 1/Semester 1a/Introduction to Logic/2019 Paul Bricman (Notes).pdf]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/L1.5.pdf]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/L1.pdf]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/L2.pdf]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/L3.pdf]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/L4.pdf]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/L5.pdf]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/L6.pdf]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/L7.pdf]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/L8.pdf]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/LPL textbook.pdf]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/hw2-2026.pdf]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/logic-cnf-dnf.pdf]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/quantifier-quiz.pdf]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/syllabus-2023-2024-Ma-AI.pdf]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/syllabus-2023-2024-Ma-AI_1.pdf]]
* [[Courses/Year 1/Semester 1a/Introduction to Logic/worksheet2.pdf]]
<!--/lua-->