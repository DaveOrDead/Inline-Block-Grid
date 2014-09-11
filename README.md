# Inline-Block-Grid

A fluid, responsive, lightweight, simple, SCSS based inline block grid

## Credits

This would not have been possible without heavy influence drawn from the following grid systems:

* Harry Roberts [InuitCSS Grid](https://github.com/inuitcss/objects.layout)

* Bourbon's [Neat](http://neat.bourbon.io/) grid

## Why this grid?

### Clean markup

I am a huge advocate of using meaningul and semantic class names in my mark up - I hate the idea of having classes called .col1 etc cluttering my HTML.   This can get very confusing at smaller sizes when .col6 classes start behaving like .col12 because of a media query.  This grid system uses SCSS silent extends which allow you to abstract the layout styles away into your CSS, meaning you can use your own class names.

e.g
HTML
```html
<section class="your-classname-here">

    <div class="whatever-classname-you-want">

    </div>

    <div class="whatever-classname-you-want">

    </div>

</section>
```

SCSS
```css
.your-classname-here {
  @extend %grid;
}
.whatever-classname-you-want{
  @extend %grid__item;
  @include cells(4);
}
```


###  Lightweight

Again using the power of silent extends means the grid classes sit ‘invisibly’ in your Sass and only get compiled to CSS when used.

###  No need to worry about floats!

This grid system takes advantage of the benefits of inline-block which means you don't have to worry about clearing floats or applying .last or .omega classes to the final column in each row.

### Fully responsive and Fluid

A percentage width based approch means the grid is totally fluid.  Using simple media queries you can change the width of each cell by simply updating a number.