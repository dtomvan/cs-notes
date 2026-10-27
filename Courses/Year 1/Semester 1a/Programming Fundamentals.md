---
pageDecoration: 
  icon: book-open
tags: course
---
# Programming fundamentals

- Ocasys: https://ocasys.rug.nl/current/catalog/course/WBCS046-10
- Lecturer: Dr. Arnold Meijster
- Mail: [a.meijster@rug.nl](mailto:a.meijster@rug.n) but preferably [progfunrug@gmail.com](mailto:progfunrug@gmail.com)
- Books
  - Program Proofs (https://u.toostveen.nl/dafny)
  - ANSI C (by Ritchie himself)
  - Reader (https://u.toostveen.nl/ipinc)
- Reit: HW at [Themis](https://themis.housing.rug.nl)
- Assessment:
  - 3 subexaminations (mean of them needs to be 5)
  - lab sessions (mean of them needs to be 5)
  - final grade: mean of the above 2

---

- [[Courses/Year 1/Semester 1a/Programming Fundamentals/styleguideC.pdf|Style Guide]]
- [[Courses/Year 1/Semester 1a/Programming Fundamentals/IPinC2627.pdf|Imperative Programming in C]]
- [[]]

Weekly notes:

${query[[
  from p = index.contentPages("week")
  where p.parentCourse == "[[" .. editor.getCurrentPage() .. "]]"
  select templates.pageItem(p)
]]}

PDFs:
${query [[
  from p = index.documents()
  where string.startsWith(p.name, editor.getCurrentPage()) and p.contentType == "application/pdf"
  select templates.pageItem(p)
]]}
