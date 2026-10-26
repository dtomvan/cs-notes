---
tags: "meta/template/page"
## Uncomment any of the single-commented lines to set options
#############################################################
## Offer a suggested name when triggered
suggestedName: "${editor.getCurrentPage()}/Week "
## Whether or not to confirm the suggestedName or go there directly
confirmName: true
## To open a page if it already exists rather than create it fresh
#openIfExists: true
## To trigger the page template with a custom command
command: Create Week
## To trigger the page template with a custom key
#key: "Ctrl-q c"
#mac: "Cmd-Alt-q"
## To prefill frontmatter
frontmatter: |
  date: "${date.today()}"
  pageDecoration:
    icon: airplay
  tags: week cs/COURSE_ID
  parentCourse: "[[${editor.getCurrentPage()}]]"
  
## To manage the order in which the page templates appear
#priority: 10
---
# ${utils.getPageName(editor.getCurrentPage())}

## Lecture |^|

- Date: ${date.today()}
- Topic: 
