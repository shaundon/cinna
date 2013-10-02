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

## Mixins

### Naming

Use camelCase for naming your mixins. For example:

```
mixinName() {
	property: value;
}
```
This allows you to distinguish at a glance between standard CSS properties, which are named like `border-radius`, and a mixin, which would be called `borderRadius`.







