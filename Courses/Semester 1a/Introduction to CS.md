---
  pageDecoration:
    icon: book-open
  tags: coursecs/COURSE_ID
---
# Introduction to CS

- Ocasys: https://ocasys.rug.nl/current/catalog/course/WBCS005-05
- Book: https://u.toostveen.nl/ics

---

- Lectures: 2h a week
- HW: every week in brightspace
- Online quizzes
- Programming project (choice!)
- Written exam

---

<!--#lua query[[
  from p = index.contentPages("week")
  where p.parentCourse == "[[" .. editor.getCurrentPage() .. "]]"
  select templates.pageItem(p)
]] -->
* [[Courses/Semester 1a/Introduction to CS/Week 1]]
* [[Courses/Semester 1a/Introduction to CS/Week 2]]
* [[Courses/Semester 1a/Introduction to CS/Week 3]]
<!--/lua-->

<!--#lua query [[
  from p = index.documents()
  where string.startsWith(p.name, editor.getCurrentPage()) and p.contentType == "application/pdf"
  select templates.pageItem(p)
]] -->
*(empty table)*
<!--/lua-->
