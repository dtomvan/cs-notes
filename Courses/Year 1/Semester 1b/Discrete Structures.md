---
  pageDecoration:
    icon: book-open
  tags: course
---

# Discrete structures

- Ocasys: https://ocasys.rug.nl/current/catalog/course/WBCS011-05#WBCS011-05.2026-2027.1
- Book: https://u.toostveen.nl/dms
- Lectures: 
- Tutorials: 
- Assessment: 
- Software: 

---

Weekly notes:

${
query[[
  from p = index.contentPages()
  where string.startsWith(p.ref, editor.getCurrentPage() .. "/")
  select templates.pageItem(p)
]]
}

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