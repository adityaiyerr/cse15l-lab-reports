## Lab Report 5

# I found the tests with different results using the vimdiff command.

As shown in Lab 9, the following ahs an example of what the vimdiff command looks like.
![Image](lab5image1.png)

# [Test 201.md](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/201.md)

For Test 201, my implementation was correct, outputting `[]` , while the provided implementation outputted `[baz]`. Using VSCode preview, I know that there should be no link showing in the output, because there are no links in the actual test file.

The outputs of both files can be seen here, with my implementation showing a `[]` while the given implementation showing `[baz]`, with the expected output being `[]`.
![Image](lab5image3.png)
![Image](lab5image4.png)

VSCode preview shows what it should produce:
![Image](lab5image2.png)

The provided implementation recognized the open and closing parentheses and assumed that the contents inside were a link. However, this was not the case for test 201. A fix for this problem would be to make the implementation check for the closing bracket and opening parenthesis right after one another and then look for the closing parenthesis to make sure that there are characters (that aren't white spaces) between the closing bracket and opening parenthesis.

Using my lab mate, Davit Margarian's markdown parser, I can identify that the fix to the code can be implemented within the following code block:
![Image](lab5image8.png)

# [Test 14.md](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/14.md)

For Test 14, my implementation was correct, outputting `[]`, while the provided implementation outputted `[foo]`. Using VSCode preview, I know that there should be no link outputted because there are no links within the test file itself.

The outputs of both files are shown here:
![Image](lab5image6.png)
![Image](lab5image7.png)

VSCode preview shows what links it should produce:
![Image](lab5image5.png)

The provided implementation does not check for backslashes, so by making it check for backslashes, it can skip over those and move on to find the rest of the link within the parentheses. This is similar to the fix made to check for backticks in a previous lab, only now it is checking for backslashes instead.

Similar to the last test, the change implementation would be in the same section of the code, specifically in the while loop, checking for any abnormalities in the url.
![Image](lab5image8.png)
