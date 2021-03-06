# CSS and SASS

## Basics

* CSS 1 (~1996), CSS 2 (~1998) and CSS 3 is the latest version (still in development) and we will never get CSS 4 since it has already branched into different modules such as animations, grids, flex etc.

* Chrome browser displays the CSS rules as per the `specificity`.

* If the rules have the same specificity (precedence) then the order of CSS rule takes the decision.

* Every element is displayed as a box. `Contents + Padding + Border + Margin` together makes the box model.

* If the padding is added to the parent element then the margin of the child element lies under the padding.

* Body has a default margin of 8px on chrome. Actually, every element has a default browser margin.

* **Margin Collapsing** When two boxes are adjacent and they have margin then their margins collapse and the biggest margin wins and gets shown between them. Basically, they are _not added_.

* In shorhand property writing the order doesn't matter as long as there are no conflicts of the values.

* `Box Sizing` is `content-box` by default. We can make it `border-box` but it will still not include the margin.

* You use universal selector `* {...}` if you don't want your styling to be overriden by the broswer defaults since it does not use inheritance instead it applies the style to all the elements.

> Universal specificity has lowest/zero specificity (0,0,0,0)

* Rely more on specificity than order for more maintainable CSS

```javascript
Inline elements:

1. respect left & right margins and padding, but not top & bottom
2. cannot have a width and height set
3. allow other elements to sit to their left and right.
4. see very important side notes on this here.

Block elements:

1. respect all of those
2. force a line break after the block element
3. acquires full-width if width not defined

Inline-block elements:

1. allow other elements to sit to their left and right
2. respect top & bottom margins and padding
3. respect height and width
```

![Pseudo](./images/pseudo.png 'Pseudo Class Vs Element')

* `CTA` call to action - Generally a button that triggers some action e.g. Register/Login Or Start Hosting or Try Now/Download etc.

* Always check CSS compatibility on `MDN` and `caniuse.com`

* If you define your fonts in `px` then when you increase/decrease the browser font size you won't see any effect and that's not OK! Also, when you zoom in, the overall layout is at risk. Better use font relative units e.g. root em (rem) and em (the size of widest character M).

  > rem is not supported for < IE 9

![Units](./images/units.png 'Which unit should I use?')

![Units Summary](./images/summary.png 'Summary')

* `margin: auto;` works only for block level elements with explicitlt defined width.

* It is a recommended that if you have to apply styles/positioning on inline elements then first put them inside block elements e.g. a div and then add classes.

* text-align works on inline/inline-block elements.

![3 Pillars](./images/pillars.png '3 Pillars of CSS')

* Biggest performance comes out of minimal use of images.

* `CSSOM`: CSS Object Mofel

* Specificity In Action
  ![specificity](./images/specificity.png 'Specificity')

* Root font size is defined in the html element. It's a good practise to defined it to 10px (i.e. 10/16 = `62.5%`) in html selector (for ease of calculation) and make all values rem.

* `background-image/color` occupies the padding too.

* `z-index` works for both absolute and relative positioning.

* `transition`, `opacity` value different from 1, a `filter` also creates stacking context and not just the z-index.

* BEM Block Element Modifier

  Benefits:

  1.  Results in low specificity classes (better performance, avoid CSS collisions) since classes are not nested.

  Great Read:

  https://seesparkbox.com/foundry/bem_by_example

* The default `display` value for all elements is "`inline`". Most "User Agent stylesheets" (the default styles the browser applies to all sites) reset many elements to "`block`". More: https://css-tricks.com/almanac/properties/d/display/

* Pseudo element is treated as a child element.

* Unlike normal CSS we can mix units in SASS for `calc()`

* When all the elements of the container `float` then the height of the container becomes `0`. To fix this we need `clearfix`

* `inline` elements are treated like text so you can apply css properties such as `text-align: center;`

## SASS

* SASS is a tool (a Ruby Gem). CSS on steroids. Browser can't understand SASS. More condenced and easier to maintain.

* There are two syntaxes available for Sass. The new main syntax (as of `Sass 3`) is known as “SCSS” (for “Sassy CSS”), and is a superset of CSS3's syntax. This means that every valid CSS3 stylesheet is valid SCSS as well. SCSS files use the extension .scss. The second, older syntax is known as the `indented syntax` (or just “Sass”)

* SCSS has the same feature but feels more close to native CSS and more natural than SASS syntax which works on indentation basis with no semicolons and curly braces.
