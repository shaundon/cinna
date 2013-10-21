# Tables

## When To Use Tables

Tables are for displaying tabular data, like charts of data or statistics. As a rule of thumb, use them for things that you would place in a spreadsheet.

Tables should not be used for layout. People who still argue this should be referred to the [W3's recommendations from 2000](http://www.w3.org/TR/2000/NOTE-WCAG10-HTML-TECHS-20001106/#tables-layout), then fed to lions.

### CSS Tables

Although you should really be able to function without layout tables, CSS tables are acceptable. This is where you style some other elements to behave like a table layout.

#### Why Is this OK?

The main problem with layout tables is that they betray semantics by using HTML designed for one purpose for an entirely different purpose. CSS tables don't do this, as the HTML elements used won't be tables. 

## Headings

Be sure to use the <code>th</code> element for headings, instead of just using a <code>td</code> that's been styled to look different.

## Optional elements

<code>thead</code>, <code>tbody</code> and <code>tfoot</code> are all optional elements, but if you're unsure whether to include them, err on the side of caution and put them in.

