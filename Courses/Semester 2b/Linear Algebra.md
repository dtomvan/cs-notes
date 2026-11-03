---
pageDecoration:
  icon: book-open
tags: course
---
# Linear Algebra

- Ocasys: https://ocasys.rug.nl/current/catalog/course/WBCS048-05#WBCS048-05.2026-2027.1
- Book:
  - Linear Algebra and Its Applications (not required)
  - https://u.toostveen.nl/linalg
- Lecturer: Prof. Steffen Müller
- Lectures: 
- Tutorials: 
- Assessment:
  - Exam (55%)
  - Midterm (35%)
  - Homework (10%)
- Software: 

---

Weekly notes:

${
query[[
  from p = index.contentPages("week")
  where p.parentCourse == "[[" .. editor.getCurrentPage() .. "]]"
  select templates.pageItem(p)
]]
}

PDFs:

${
query [[
  from p = index.documents()
  where string.startsWith(p.name, editor.getCurrentPage()) and p.contentType == "application/pdf"
  select templates.pageItem(p)
]]
}