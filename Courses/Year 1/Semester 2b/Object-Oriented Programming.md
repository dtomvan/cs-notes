---
pageDecoration:
  icon: book-open
tags: course
---
# Object-Oriented Programming

- Ocasys: https://ocasys.rug.nl/current/catalog/course/WBCS028-05#WBCS028-05.2026-2027.1
- Book:
  - Absolute Java, sixth edition, https://u.toostveen.nl/absolutejava
  - Design Patterns: Elements of Reusable Object-Oriented Software, https://u.toostveen.nl/designpat
- Lecturer: dr A. Rastogi
- Lectures:
- Tutorials: 
- Assessment:
  - Group project (need 5)
  - Homework (need 5)
  - Exam (need 5)
  - Need mean 6
- Software: IntelliJ Idea :(

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