---
  pageDecoration:
    icon: book-open
  tags: course
---

# Computer Architecture

- Ocasys: https://ocasys.rug.nl/current/catalog/course/WBCS010-05#WBCS010-05.2026-2027.1
- Book: https://u.toostveen.nl/carch
- Lectures: Monday (FB95), Tuesday (EA29)
  - **December 7**: BB151
- Assessment:
  - Assignments
    - Assignment 1: due 2026-11-30
    - Assignment 2: due 2026-12-11
    - Assignment 3: due 2027-01-15
  - Final
  - Labs will be just for receiving feedback

---

Weekly notes:

<!--#lua query[[
  from p = index.contentPages("week")
  where p.parentCourse == "[[" .. editor.getCurrentPage() .. "]]"
  select templates.pageItem(p)
]] -->
* [[Courses/Year 1/Semester 1b/Computer Architecture/Week 1]]
* [[Courses/Year 1/Semester 1b/Computer Architecture/Week 2]]
<!--/lua-->

PDFs:

<!--#lua 
query [[
  from p = index.documents()
  where string.startsWith(p.name, editor.getCurrentPage()) and p.contentType == "application/pdf"
  select templates.pageItem(p)
]]
 -->
* [[Courses/Year 1/Semester 1b/Computer Architecture/A1.pdf]]
* [[Courses/Year 1/Semester 1b/Computer Architecture/L1.pdf]]
* [[Courses/Year 1/Semester 1b/Computer Architecture/L2.pdf]]
<!--/lua-->