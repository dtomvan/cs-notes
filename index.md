This now runs [Silverbullet](https://silverbullet.md). Partly replaces copyparty, party replaces the previous MDBook setup. How exciting.

# Year 1

${
query [[
  from p = index.contentPages("course")
  group by utils.getPageDirectory(p.name)
]]
}

## Semester 1a
- [[Courses/Semester 1a/Programming Fundamentals|Programming Fundamentals]]
- [[Courses/Semester 1a/Introduction to Logic|Introduction to Logic]]
- [[Courses/Semester 1a/Introduction to CS|Introduction to CS]]
## Semester 1b
- [[Courses/Semester 1b/Computer Architecture|Computer Architecture]]
- [[Courses/Semester 1b/Discrete Structures|Discrete Structures]]