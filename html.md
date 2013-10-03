# HTML

## Semantic Naming

Name your classes and IDs semantically. For example, this might be great when your page is first written:

    <p class='red'>Some important info.</p>
    
<p style="color: #c00;">Some important info.</p>


But what happens when you decide to change the 'important' colour to blue? 

    <p class='red'>Some important info.</p>
    
<p style="color: #08c;">Some important info.</p>

A semantic naming convention can make this better:

    <p class="important">Some important info.</p>
    
## Strict HTML

The HTML5 spec doesn't enforce attributes enclosed in quotes. So, this is valid:

    <span class=foo>Hello world</span>
    
However, this can potentially cause issues. If you wanted to add the `important` class from earlier to this element to change the colour, it would become:

    <span class=foo important>Hello world</span>
    
The browser will interpret `important` as an attribute, not a class, and it won't be applied.

Using quotes on your attributes eliminates this risk:

    <span class="foo important">Hello world</span>
    
    
## Tables

Tables should only be used for tabular data, not layout.

If you wouldn't put it in a spreadsheet, don't put it in a table.

### CSS Tables

CSS tables are ok. One of the main problems with using a HTML table inappropriately is that it's not semantic. With CSS, you can mark up other elements, like `<div>`s to behave like a table. As this isn't messing with semantics, it's ok.
      

