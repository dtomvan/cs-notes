---
pageDecoration:
  icon: book-open
tags: course
---
# Introduction to Information Systems

- Ocasys: https://ocasys.rug.nl/current/catalog/course/WBCS021-05#WBCS021-05.2026-2027.1
- Book:
  - Fundamentals of Database Systems, 7th Edition, 2006
  - 
- Lectures: 
- Tutorials: 
- Assessment: 
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