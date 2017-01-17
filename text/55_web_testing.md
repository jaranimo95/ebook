# Automated Web Testing

So far, all of the systems under test that we've discussed have used a simple, text-based interface.  It turns out that in the years since 1965, many users have decided that they want graphical, touch-based, or other ways of interacting with a system.  Testing these, especially in an automated fashion, can often be more difficult than a traditional text interface.

We can do automated systems-level tests using a variety of tools.  In this chapter, we'll discuss testing web sites using a tool called Selenium.  The point of this chapter is not to make you an expert in using Selenium, though.  It's to give you the necessary foundation to write automated tests for any application with a more complicated interface than text.  Many of the techniques we will discuss 

## Theory of Testing Graphical Interfaces

The key idea to keep in mind is that we are still testing, even if the interface is different than the ones we have encountered so far.  That is, we are still checking to see that the expected behavior of the system under certain circumstances is the same as the observed behavior.  This expected behavior may be more complicated to explain or to check, or we may discuss it in a more abstract manner, but there are always ways to determine to define the expected behavior and to observe if it actually occurs.

For example, for a text-based interface, one can always copy and paste the expected and observed text.  Comparisons are simple - you can check visually or, for more lengthy output, use a tool like Unix's `diff` or write a simple program to verify that the text is correct.  This becomes difficult to do when interacting with graphical programs, web pages, and the like.  The expected behavior might be something such as "an error message will appear in the center of the screen, with a picture of a bug with a slash through it".  How do we programmatically check such a complicated explanation of the expected behavior?

One possibility is to simply examine the HTML code of the page and ensure that it matches the known HTML which will display the picture of the bug, that centers it properly, and all of the other criteria.  That is, imagine some JUnit pseudocode like this:

```java
@Test
public void testCenteredBugMessage() {
    String
    String expectedHtml = “<!DOCTYPE html><html lang="en-US"><head><title>No Bug Page</title></head><body><div><img src=\"bugslash.jpg\" alt="Bug with Slash Through It" height="50" width="50"><strong>No bug allowed here!</strong></div></body>"; 
    // Assume the getHtml() method is a helper method to get the 
    // raw HTML returned from a URL
    String pageHtml = getHtml("http://example.com"); 
    assertEquals(expectedHtml, pageText); 
}
```

This will check that the page has the right HTML, and assuming we wrote it correctly, then if the test passes, our page is being displayed correctly.  There are a few problems with testing complex interfaces this way, though.

_It's fragile_ - If anything on the page changes, the entire test is invalid.  For example, let's make a 

_It's at the wrong level of abstraction_ - If I were talking to another person about what I wanted on a web page, I certainly wouldn't start with "well, first I want a `<` sign, and then a `!`, and then the word DOCTYPE, and then a space..."  I wouldn't even say something
Kind of like programming in assembly

_It's unreadable_ - 

_There's no semantic understanding_ -  (e.g. of links, textboxes)

_What about JavaScript and CSS?_ - This is mostly specific to web pages and not all graphical display formats, but JavaScript and CSS can dynamically modify HTML or how it is displayed.  In order to check 



Also check that the right JS is on page?

