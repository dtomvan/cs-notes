${mermaid.diagram(mermaid.relationGraph{
  pages = query[[from index.contentPages() where table.includes(tags, "course") or _.parentCourse ]],
  relations = {"parentCourse"},
})}
