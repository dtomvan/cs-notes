---
pageDecoration:
  icon: book-open
tags: course
---
# Calculus 1

- Ocasys: https://ocasys.rug.nl/current/catalog/course/WBCS055-05
- Book:
  - Calculus, Early Transcendentals, International Metric Edition (9th edition)
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