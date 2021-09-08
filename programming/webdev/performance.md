# Performance

User has 2 steps while the page is rendering:

1. Partially interaction with the page \(**FMP** - First meaningful paint\)
2. Full interaction with the page \(**TTI** - Time to interactive\)

**FMP** -  HTML is loaded, text is loaded. User can read content without interaction.

**TTI** - web page is ready for use, scripts are loaded.

**FMP** one of the main metrics which describes **Critical render path.**

### Critical render path

**Critical render path -** set of actions and resources that browser should perform, download and process in order for the user to get their first workable result. \(load HTML, CSS\).

1. Request HTML
2. Receive an HTML
3. Parse the HTML
4. Build a DOM tree
5. Request for CSS
6. Receive CSS
7. Build CSS tree
8. Run JS code
9. Rebuild DOM if needed
10. Build render tree
11. Paint the page \(layout -&gt; paint -&gt; Composite\)



