# Stylus Files

## Syntax Format

Stylus allows for a minimal syntax, that looks like this:

```
selector
	property: value
```
and a more verbose syntax:

```
selector {
	property: value;
}
```

The second, more verbose syntax is identical to vanilla CSS, with the exception that you can take advantage of some of Stylus's features, like nesting:

```
selector {
	property: value;
	
	&:hover {
		property: value;
	}
}
```

Use the second, verbose syntax. This allows for consistency when importing external CSS. For example, let's say you have an external CSS library named `awesomestyles.css`, and you want to include it in your Stylus files. You can drop it right in to your code and it'll match your Stylus syntax.

## Braces

Place braces on the same line as the rule beginning:

```
selector {
    property: value;
}
```

as opposed to:

```
selector
{
    property: value;
}
```

Always use the expanded syntax, and never the abbreviated one line version:

```
selector { property: value; } /* Don't use this! */
```

## Ordering Properties

Order properties alphabetically:

```
selector {
    border: 1px solid #ccc;
    height: 70px;
    text-align: center;
    width: 120px;
}
```
### Vendor Prefixes

When using vendor prefixes, order them alphabetically, except with the W3C version last. This is because properties are read sequentially, so when a property becomes implemented as standard it will automatically supercede the vendor prefixed version.

However, vendor prefixes should appear alphabetically with other properties, ignoring the prefix. For example:

```
selector {
    border: 1px solid #ccc;
    height: 70px;
    text-align: center;
    -moz-transition: all 0.1s;
    -ms-transition: all 0.1s;
    -o-transition: all 0.1s;
    -webkit-transition: all 0.1s;
    transition: all 0.1s;
    width: 120px;
}
```

However, if you're using vendor prefixes, you should probably take advantage of a mixin.

#### Which Prefixes To Use

As of October 2013, the vendor prefixes in use are:

* `-moz-` - Mozilla Firefox, other Mozilla renderers.
* `-ms-` - Microsoft Internet Explorer, other Microsoft browsers.
* `-o-` - Opera. Note that Opera has switched to use Blink, Chrome's rendering engine, so this will become obsolete soon.
* `-webkit-` - Apple Safari, for OS X and iOS, older versions of Chrome and Android, Blackberry browser, some other webkit implementations.

Google Chrome has been forked from webkit, and has taken a policy of implementing without prefixes, just the standard property.


## Spacing

Use four spaces, for example:

```
selector {
    property: value;
}
```

## Multiple Selectors

Place multiple selectors within one rule on new lines:

```
h1,
h2,
h3 {
    border-bottom: 1px solid #aaa;
}
```

## Shorthand Properties

Use shorthand where it makes sense. For example:

```
h1 {
    border: 1px solid #aaa;
}
```

is much clearer than:

```
h1 {
    border-color: #aaa;
    border-style: solid;
    border-width: 1px;
}
```
However, if you only want to override a single property, it's better to just use the second style, to make it clear that's all that's changing. For example:

```
.column {
    border: 1px solid #ccc;
    
    a {
        border-color: #369;
    }
}
```

When defining four directions of a property at once, think of **TRouBLed** - Top, Right, Bottom, Left. E.g.:

```
margin: 5px 0 3px 2px;
```

is the same as:

```
margin-top: 5px;
margin-right: 0;
margin-bottom: 3px;
margin-left: 2px;
```

## Units

Use percentages for larger elements where appropriate, although pixels are acceptable for smaller things, for example margins and padding.

When using zero, don't include a unit, as there's no point. 0px = 0em = 0pt = 0%. So just use 0.


## Mixins

### Naming

Use camelCase for naming your mixins. For example:

```
mixinName() {
	property: value;
}
```
This allows you to distinguish at a glance between standard CSS properties, which are named like `border-radius`, and a mixin, which would be called `borderRadius`.

## Colours

### Hex vs RGB vs HSL

Hex colours are generally easier to read than RGB and HSL, so use these. However, there's a potential problem - hex colours don't support transparency, like RGBA and HSLA do. You can circumvent this by using one of Stylus's built in functions:

```
color: rgba(#08c, 0.9);
```

compiles to:

```
color: rgba(0, 136, 204, 0.9);
```

### Shorthand Notation

Where possible, use the shorthand version of hex colours. For example `#9933aa` can be truncated to `#93a`.

### Casing

For consistency, stick to lowercase for colours, e.g. `#fef` over `#FEF`.

## Naming

Name elements semantically. For example, let's say you have a class used to denote if something is important:

```
.red {
    color: #c00; /* Red */
}
```

Then, you decide that the 'important' colour will now be blue, so you end up with:

```
.red {
    color: #08c; /* Blue */
}
```

To get around this, use semantic names:

```
.important {
    color: #c00;
}
```


## Property Status

### rgba

`rgba` is now supported by all decent browsers, and IE9 onwards. Therefore, if you desperately need IE8 support, simply add a fallback:

```
selector {
    background: rgb(127, 127, 127);
    background: rgba(127, 127, 127, 0.6);
}
```

An approach for this in the past would have been to add a fallback that emulates opacity. For example, if you have a dark blue colour, with 40% transparency, it looks like light blue, so the `rgb` fallback would be set to the light blue colour, giving an approximation. With IE8 usage declining, it's recommended to no longer do this, and save time by using the earlier method of just adding the same colour with no alpha channel.









