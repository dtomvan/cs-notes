# Computer Architecture

- Ocasys: https://ocasys.rug.nl/current/catalog/course/WBCS010-05#WBCS010-05.2026-2027.1
- Book: https://u.toostveen.nl/carch
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

${
query [[
  from p = index.documents()
  where string.startsWith(p.name, editor.getCurrentPage()) and p.contentType == "application/pdf"
  select templates.pageItem(p)
]]
}