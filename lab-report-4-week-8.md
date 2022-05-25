## Lab Report 4

# [Link to my Markdown Repository](https://github.com/UDXS/markdown-parser)

# [Link to the reviewed Markdown Repository](https://github.com/canitry/cse15l-lab-reports)

# For Snippet 1:

Using VSCode Preview, I expected there to be an error since the first url did not show up as a hyperlink.

Test Code on my repository:
`@Test
  public void testSnippet1() throws Exception {
    ArrayList<String> links = MarkdownParse.getLinks(Files.readString(Path.of("test-file9.md")));
    String[] expected = {};
    assertArrayEquals(expected, links.toArray());
  }`
  
