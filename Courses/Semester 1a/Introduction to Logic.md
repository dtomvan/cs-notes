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

Weekly notes:
<!--#lua query[[
  from p = index.contentPages("week")
  where p.parentCourse == "[[" .. editor.getCurrentPage() .. "]]"
  select templates.pageItem(p)
]] -->
* [[Courses/Semester 1a/Introduction to Logic/Week 1]]
* [[Courses/Semester 1a/Introduction to Logic/Week 2]]
* [[Courses/Semester 1a/Introduction to Logic/Week 3]]
* [[Courses/Semester 1a/Introduction to Logic/Week 4]]
* [[Courses/Semester 1a/Introduction to Logic/Week 5]]
* [[Courses/Semester 1a/Introduction to Logic/Week 6]]
* [[Courses/Semester 1a/Introduction to Logic/Week 7]]
<!--/lua-->

PDFs:

${query [[
  from p = index.documents()
  where string.startsWith(p.name, editor.getCurrentPage()) and p.contentType == "application/pdf"
  select templates.pageItem(p)
]]}