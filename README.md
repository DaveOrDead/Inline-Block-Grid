# Inline Block Grid

A fluid, responsive, lightweight, simple, SCSS based inline block grid.

If you can't be bothered to read all the below you can just jump straight into the Codepen demo and play around: [Inline Block Grid Demo](http://codepen.io/davislurve/pen/Azfqb

## Credits

This would not have been possible without heavy influence drawn from the following grid systems:

* Harry Roberts [InuitCSS Grid](https://github.com/inuitcss/objects.layout)

* Bourbon's [Neat](http://neat.bourbon.io/) grid

## Why this grid?

### Clean markup

I am a huge advocate of using meaningul and semantic class names in my mark up - I hate the idea of having classes called .col1 etc cluttering my HTML.   This can get very confusing at smaller sizes when .col6 classes start behaving like .col12 because of a media query.  This grid system uses SCSS silent extends which allow you to abstract the layout styles away into your CSS, meaning you can use your own class names.

###  Lightweight

Again using the power of silent extends means the grid classes sit ‘invisibly’ in your Sass and only get compiled to CSS when used.

###  No need to worry about floats!

This grid system takes advantage of the benefits of inline-block which means you don't have to worry about clearing floats or applying .last or .omega classes to the final column in each row.

### Fully responsive and Fluid

A percentage width based approch means the grid is totally fluid.  Using simple media queries you can change the width of each cell by simply updating a number.

### Infinite nesting

Pretty much as the title says, you can nest as many times as you like and it won't break.

### Flexible

Options are included to push or pull cells, reverse their ordering, switch gutter widths on the fly etc.  Check out the options section below.

### Easy to use

Simply adjust one number to change cell spans

## Examples

### Basic Mark up

HTML
```html
<section>
  <aside>What's this thing I've found?</aside><!--
  --><article>Just an awesome, responsive, semantic grid framework built on top of Sass</article>
</section>
```

SCSS
```scss
section {
  @extend %grid;
}
aside {
    @extend %grid__item;
    @include cells(3);
 }
article  {
    @extend %grid__item;
    @include cells(9);
 }
```

### Media Queries

This example shows how both elements could convert to full width below 700px

SCSS
```scss
section {
  @extend %grid;
}
aside {
    @extend %grid__item;
    @include cells(3);
 }
article  {
    @extend %grid__item;
    @include cells(9);
 }

@media all and (max-width: 699px) {
    aside {
        @include cells(12);
    }
    article {
        @include cells(12);
    }
}
```

## Options

### Gutters

Instead of using @extend %grid; you can use the following to alter the gutters

* @extend %grid--narrow;    // gives you thinner gutters
* @extend %grid--wide;       // gives you wide gutters
* @extend %grid--full;         // full width cells with no gutters
* @extend %grid--rev;         // flips the order of the cells in the grid to run right to left

### Pushing and pulling

Grid items can be pushed or pulled by a number of cells by including push or pull classes.  Example below.

SCSS
```scss
section {
  @extend %grid;
}
aside {
    @extend %grid__item;
    @include cells(2);
    @include push(1);
 }
article  {
    @extend %grid__item;
    @include cells(7);
    @include pull(2);
 }
```

## Things to be aware of

* This is a twelve column grid
* Inline-block needs white space removed between elements. (I tend to use comments to achieve this as per the example above)
* Box-sizing: border-box; is required on all grid elements or it won't work.  I tend to blanketly apply this class to all elements anyway so it's not an issue for me, if not, you'll want to add this in.