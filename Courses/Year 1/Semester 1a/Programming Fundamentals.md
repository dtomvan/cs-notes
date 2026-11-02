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
- [[Courses/Year 1/Semester 1a/Programming Fundamentals/Style tips]]

Weekly notes:

<!--#lua query[[
  from p = index.contentPages("week")
  where p.parentCourse == "[[" .. editor.getCurrentPage() .. "]]"
  select templates.pageItem(p)
]] -->
* [[Courses/Year 1/Semester 1a/Programming Fundamentals/Week 2]]
* [[Courses/Year 1/Semester 1a/Programming Fundamentals/Week 3]]
* [[Courses/Year 1/Semester 1a/Programming Fundamentals/Week 4]]
* [[Courses/Year 1/Semester 1a/Programming Fundamentals/Week 6]]
* [[Courses/Year 1/Semester 1a/Programming Fundamentals/Week 7]]
<!--/lua-->

PDFs:
<!--#lua query [[
  from p = index.documents()
  where string.startsWith(p.name, editor.getCurrentPage()) and p.contentType == "application/pdf"
  select templates.pageItem(p)
]] -->
* [[Courses/Year 1/Semester 1a/Programming Fundamentals/IPinC2627.pdf]]
* [[Courses/Year 1/Semester 1a/Programming Fundamentals/PFweek1.pdf]]
* [[Courses/Year 1/Semester 1a/Programming Fundamentals/PFweek2.pdf]]
* [[Courses/Year 1/Semester 1a/Programming Fundamentals/PFweek3.pdf]]
* [[Courses/Year 1/Semester 1a/Programming Fundamentals/PFweek4.pdf]]
* [[Courses/Year 1/Semester 1a/Programming Fundamentals/handoutsDafny1.pdf]]
* [[Courses/Year 1/Semester 1a/Programming Fundamentals/handoutsDafny2.pdf]]
* [[Courses/Year 1/Semester 1a/Programming Fundamentals/lab2PF2627.pdf]]
* [[Courses/Year 1/Semester 1a/Programming Fundamentals/lab3PF2627.pdf]]
* [[Courses/Year 1/Semester 1a/Programming Fundamentals/lab4PF2627.pdf]]
* [[Courses/Year 1/Semester 1a/Programming Fundamentals/lab5PF2627.pdf]]
* [[Courses/Year 1/Semester 1a/Programming Fundamentals/resit1PF2526.pdf]]
* [[Courses/Year 1/Semester 1a/Programming Fundamentals/styleguideC.pdf]]
<!--/lua-->
