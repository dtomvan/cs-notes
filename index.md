“Lite” version of this website (SSR, no LaTeX or other fancy stuff) at: https://cs-mini.toostveen.nl (run ${widgets.commandButton("Navigate: Open in cs-mini.toostveen.nl")} anywhere)

# Year 1
- [Copyparty](https://fs.toostveen.nl/pub/UG/CS-1) (only for books, most content will live here now)

## Semester 1a
- [[Courses/Year 1/Semester 1a/Programming Fundamentals|Programming Fundamentals]]
- [[Courses/Year 1/Semester 1a/Introduction to Logic|Introduction to Logic]]
- [[Courses/Year 1/Semester 1a/Introduction to CS|Introduction to CS]]
## Semester 1b
- [[Courses/Year 1/Semester 1b/Computer Architecture|Computer Architecture]]
- [[Courses/Year 1/Semester 1b/Discrete Structures|Discrete Structures]]
## Semester 2a
- [[Courses/Year 1/Semester 2a/Algorithms and Data Structures in C|Algorithms and Data Structures in C]]
- [[Courses/Year 1/Semester 2a/Calculus 1|Calculus 1]]
- [[Courses/Year 1/Semester 2a/Introduction to Information Systems|Introduction to Information Systems]]
## Semester 2b
- [[Courses/Year 1/Semester 2b/Computer Networks|Computer Networks]]
- [[Courses/Year 1/Semester 2b/Linear Algebra|Linear Algebra]]
- [[Courses/Year 1/Semester 2b/Object-Oriented Programming|Object-Oriented Programming]]

# Changelog
See also the [[Changelog|full changelog]].

Latest entry:
${
query[[
  from index.objects("item")
  where page == "Changelog" and not parent
  order by pos desc
  limit 1
]]
}
![[Changelog$latest]]