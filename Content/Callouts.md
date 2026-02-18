User documentation: https://help.obsidian.md/Editing+and+formatting/Callouts

## Types

As of v0.14.0, Obsidian supports callout blocks, sometimes called "admonitions". Callout blocks are written as a blockquote, inspired by the "alert" syntax from Microsoft Docs.

By default, there are 12 built-in callout types, each with several aliases. Each type comes with a different background color and icon.

Any unrecognized type will default to the "note" type, unless they are [[#Custom callouts|customized]]. The type identifier is case-insensitive.

- note
- abstract, summary, tldr
- info, todo
- tip, hint, important
- success, check, done
- question, help, faq
- warning, caution, attention
- failure, fail, missing
- danger, error
- bug
- example
- quote, cite

## Built-in callout types

If an unknown type is specified, Obsidian will default to the `note` style, unless they are [[#Custom callouts|customized]]. 

> [!unknown-type]
> Lorem ipsum dolor sit amet

> [!note]
> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus non elit diam. In est dolor, maximus in magna a, sodales interdum purus. Aliquam consectetur ex at ex consequat aliquam. 

---

> [!abstract]
> Aliases: `summary`, `tldr`
> 
> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus non elit diam. In est dolor, maximus in magna a, sodales interdum purus. Aliquam consectetur ex at ex consequat aliquam.

> [!info]
> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus non elit diam. In est dolor, maximus in magna a, sodales interdum purus. Aliquam consectetur ex at ex consequat aliquam.

> [!todo]
> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus non elit diam. In est dolor, maximus in magna a, sodales interdum purus. Aliquam consectetur ex at ex consequat aliquam.

> [!tip]
> Aliases: `hint`, `important`
> 
> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus non elit diam. In est dolor, maximus in magna a, sodales interdum purus. Aliquam consectetur ex at ex consequat aliquam.

> [!success]
> Aliases: `check`, `done`
> 
> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus non elit diam. In est dolor, maximus in magna a, sodales interdum purus. Aliquam consectetur ex at ex consequat aliquam.

> [!question]
> Aliases: `help`, `faq`
> 
> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus non elit diam. In est dolor, maximus in magna a, sodales interdum purus. Aliquam consectetur ex at ex consequat aliquam.

> [!warning]
> Aliases: `caution`, `attention`
> 
> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus non elit diam. In est dolor, maximus in magna a, sodales interdum purus. Aliquam consectetur ex at ex consequat aliquam.

> [!failure]
> Aliases: `fail`, `missing`
> 
> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus non elit diam. In est dolor, maximus in magna a, sodales interdum purus. Aliquam consectetur ex at ex consequat aliquam.
> 

> [!danger]
> Alias: `error`
> 
> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus non elit diam. In est dolor, maximus in magna a, sodales interdum purus. Aliquam consectetur ex at ex consequat aliquam.

> [!bug]
> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus non elit diam. In est dolor, maximus in magna a, sodales interdum purus. Aliquam consectetur ex at ex consequat aliquam.
 
> [!example]
> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus non elit diam. In est dolor, maximus in magna a, sodales interdum purus. Aliquam consectetur ex at ex consequat aliquam.
 
> [!quote]
> Alias: `cite`
> 
> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus non elit diam. In est dolor, maximus in magna a, sodales interdum purus. Aliquam consectetur ex at ex consequat aliquam.

## Special cases

> [!tip] Callout with a custom title
> By default, the title of the callout is its type identifier in **title case**. You can change it by adding text after the type identifier:
> ```
> > [!tip] Callouts can have custom titles
> Like this one.
> ```

> [!tip] Title-only callout

## Foldable callouts

You can create a folding callout by adding `+` (default expanded) or `-` (default collapsed) after the block.

> [!faq]- Foldable callout, closed by default 
> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus non elit diam. In est dolor, maximus in magna a, sodales interdum purus. Aliquam consectetur ex at ex consequat aliquam.

> [!faq]+ Foldable callout, open by default 
> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus non elit diam. In est dolor, maximus in magna a, sodales interdum purus. Aliquam consectetur ex at ex consequat aliquam.

## Nested callouts

> [!question] Level 1
> > [!todo] Level 2 
> > > [!example] Level 3
> > 

## Custom callouts

Themes and CSS snippets may define custom callouts e.g.

```css
.callout[data-callout="my-custom-callout-type"] { 
  --callout-color: 0, 0, 0; 
  --callout-icon: lucide-alert-circle; 
}
```
will style a callout with type `my-custom-callout-type`.

`--callout-color` defines the background color using numbers (0–255) for red, green, and blue.
`--callout-icon` can be an icon ID from [lucide.dev](https://lucide.dev/), or an SVG element e.g. 
  ```css
    --callout-icon: '<svg>...custom svg...</svg>';
  ```