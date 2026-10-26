
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
${
query[[
  from p = index.contentPages()
  where string.startsWith(p.ref, editor.getCurrentPage() .. "/")
  select templates.pageItem(p)
]]
}

PDFs:

${query [[
  from p = index.documents()
  where string.startsWith(p.name, editor.getCurrentPage()) and p.contentType == "application/pdf"
  select templates.pageItem(p)
]]}