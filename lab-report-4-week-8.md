## Lab Report 4

# [Link to the Markdown Repository I used, written by Davit Margarian](https://github.com/UDXS/markdown-parser)

# [Link to the reviewed Markdown Repository](https://github.com/canitry/cse15l-lab-reports)

# For Snippet 1:

Using VSCode Preview, I expected there to be an error since the first url did not show up as a hyperlink.

Test Code:

`@Test
  public void testSnippet1() throws Exception {
    ArrayList<String> links = MarkdownParse.getLinks(Files.readString(Path.of("test-file9.md")));
    String[] expected = {"google. com',"usd.edu")};
    assertArrayEquals(expected, links.toArray());
  }`
  
Output on my repository:

`3) backTicks (MarkdownParseTest)
java.lang.AssertionError: expected:<[google.com, ucsd.edu]> but was:<[url.com,
"google. com, google.com, ucsd.edu]>
at org.junit.Assert.fail(Assert.java:88)
at org.junit.Assert.failNotEquals (Assert.java: 834)
at org.junit.Assert.assertEquals(Assert.java:118)
at org.junit.Assert.assertEquals(Assert.java:144)
at MarkdownParseTest.backTicks(MarkdownParseTest.java:69)`

Output on reviewed repository:

`3) backTicks (MarkdownParseTest)
java. lang.AssertionError: expected: <[google.com, ucsd.edu]> but was:<[ucsd. edu]>
at org.junit.Assert.fail(Assert.java:89)
at org.junit.Assert.failNotEquals (Assert.java: 835)
at org.junit.Assert.assertEquals(Assert.java:120)
at org.junit.Assert.assertEquals (Assert.java: 146)
at MarkdownParseTest.backTicks(MarkdownParseTest.java:65)`

The change to the code can be implemented in 10 lines or less because the only significant change you would have to make is to account for the backticks, which would only require adding an if statement checking for any backticks in the line.

# For Snippet 2:

Using VSCode preview and Github, I expected that the nested link in the first example of this snippet would show but the normal link in that same line wouldn't show.

Test Code:
`@Test
  public void testSnippet1() throws Exception {
    ArrayList<String> links = MarkdownParse.getLinks(Files.readString(Path.of("test-file10.md")));
    String[] expected = {};
    assertArrayEquals(expected, links.toArray("a.com","a.com(())", "example. com"));
  }`
  
Output on my repository:

`1) nestedLinks (MarkdownParseTest)
java.lang.AssertionError: expected:<[a.com, a.com(()), example.com]> but was:<[a.com, a.com((, example.com]>
at org.junit.Assert.fail(Assert.java:88)
at org.junit.Assert.failNotEquals(Assert.java:834)
at org.junit.Assert.assertEquals (Assert.java: 118)
at org.junit.Assert.assertEquals (Assert.java: 144)
at MarkdownParseTest.nestedLinks(MarkdownParseTest.java:77)`

Output on reviewed repository:

`1) nestedLinks (MarkdownParseTest)
java.lang.AssertionError: expected:<[a.com, a.com(()), example.com]> but was:<[https://something.com, some-page.html, a.com, a.com((]>
at org.junit.Assert.fail(Assert.java:89)
at org.junit.Assert.failNotEquals (Assert.java: 835)
at org.junit.Assert.assertEquals (Assert.java: 120)
at org.junit.Assert.assertEquals (Assert.java: 146)
at MarkdownParseTest.nestedLinks(MarkdownParseTest.iava:78)`

This change would most likely take more than 10 lines of code because it would require a new addition to the MarkdownParse file which accounts for the position of the nested url and also check for different separators (and the contents between them) within the line to make sure that the tester gets to all of the urls.

# Snippet 3
Using VSCode preview and Github, I expected only the second url to work, because it has an https:// before the url, which both Github and VSCode preview see as a url. Otherwise, all of the urls would have failed.

Test Code:

`@Test
  public void testSnippet1() throws Exception {
    ArrayList<String> links = MarkdownParse.getLinks(Files.readString(Path.of("test-file11.md")));
    String[] expected = {};
    assertArrayEquals(expected, links.toArray("https://sites.google.com/eng.ucsd.edu/cse-151-spring-2022/schedule");
  }`
  
Output on my repository:

`2) overOneLine(MarkdownParseTest)
java. lang.AssertionError: expected:<[https://sites.google.com/eng.ucsd.edu/cse-151-spring-2022/schedule]> but was:<[
https://www.twitter.com
https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule
github.com
And there's still some more text after that.
[this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/
]>
at org.junit.Assert.fail(Assert.java:88)
at org.junit.Assert. failNotEquals (Assert.java: 834)
at
org.junit.Assert.assertEquals (Assert.java: 118)
at org.junit.Assert.assertEquals (Assert.java: 144)
at MarkdownParseTest. over0neLine (MarkdownParseTest. java: 85)`

Output on reviewed repository:

`2) over0neLine (MarkdownParseTest)
java.lang.AssertionError: expected:<[https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule]> but was:<[]>
at org.junit.Assert.fail(Assert.java:89)
at org.junit.Assert.failNotEquals (Assert.java: 835)
at org.junit.Assert.assertEquals (Assert. java: 120)
at org.junit.Assert.assertEquals (Assert. java: 146)
at MarkdownParseTest.overOneLine(MarkdownParseTest.java:86)`

The change to the MarkdownParse.java file would be relatively easy, using 10 lines or less, because it would only require me to add an if statement that states that if there is no ending bracket or parenthesis, then it would have to use the next starting bracket or parenthesis as a placeholder for the ending of the previous url. Alternatively, if there are empty lines in the middle of the url, then I can make it so the existing loop in the MarkdownParse skips over any blank spaces, moving onto the next line.
