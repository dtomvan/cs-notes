---
tags: "meta/template/page"
## Uncomment any of the single-commented lines to set options
#############################################################
## Offer a suggested name when triggered
suggestedName: "Courses/Semester 1b/"
## Whether or not to confirm the suggestedName or go there directly
confirmName: true
## To open a page if it already exists rather than create it fresh
#openIfExists: true
## To trigger the page template with a custom command
command: Create Course
## To trigger the page template with a custom key
#key: "Ctrl-q c"
#mac: "Cmd-Alt-q"
## To prefill frontmatter
#frontmatter: |
#  date: "${date.today()}"
## To manage the order in which the page templates appear
#priority: 10
---

# |^|

- Ocasys: TODO
- Book:
- Lectures: 
- Tutorials: 
- Assessment: 
- Software: 

---

Weekly notes:

${"$"} {
query[[
  from p = index.contentPages()
  where string.startsWith(p.ref, editor.getCurrentPage() .. "/")
  select templates.pageItem(p)
]]
}

PDFs:

${"$"}{
query [[
  from p = index.documents()
  where string.startsWith(p.name, editor.getCurrentPage()) and p.contentType == "application/pdf"
  select templates.pageItem(p)
]]
}