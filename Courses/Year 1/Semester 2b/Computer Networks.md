---
pageDecoration:
  icon: book-open
tags: course
---
# Computer Networks

- Ocasys: https://ocasys.rug.nl/current/catalog/course/WBCS047-05#WBCS047-05.2026-2027.1
- Book:
  - _Self-contained_, list is not needed
  - Computer Networks (5th Ed.), https://u.toostveen.nl/cnet
  - Computer Networking: A Top-Down Approach, https://u.toostveen.nl/cnet-topdown
- Lecturer: R. Zare Hassanpour
- Lectures: 
- Tutorials: 
- Assessment:
  - Exam (60%)
  - Homework (40%)
- Software:
  - WireShark
  - Cisco Packet Tracer

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