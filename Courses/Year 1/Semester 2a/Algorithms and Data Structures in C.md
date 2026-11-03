---
pageDecoration:
  icon: book-open
tags: course
---
# Algorithms and Data Structures in C

- Ocasys: https://ocasys.rug.nl/current/catalog/course/WBCS018-05#WBCS018-05.2026-2027.1
- Book: None
- Lectures: 
- Tutorials: 
- Assessment:
  - Labs (at least 5.0)
  - Final (at least 5.0)
  - Grade: mean of above two
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