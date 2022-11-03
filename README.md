# Notes from Kevin Powell's Conquering Responsive Layouts Course
## Days 01 & 02 - `height`, `em`, and `rem`
- Avoid explicitly setting the `height` of elements.
  - Say you want more whitespace, you can utilize `padding`.
- `em` is relative to the `font-size` of a parent element.
  - It is mostly useful for buttons.
- `rem` is relative to the root `font-size`, or the one set in `html`.
- Use percentages instead of `px` for `width`.

## Day 03 - `width` and `max-width`
- The use of `width` together with `max-width`.
``` css
.container{
   width: 80%;
   max-width: 800px;
}
```
- The code above means that, for all screen sizes, the `width` of `container` should be `80%` of its parent. However, when the value of `80%` in `px` is equal or greater than `80`, the `width` should stop adjusting from there.

## Days 04 - 07 - More about the previous topics
- The use of `box-sizing: border-box`
``` css
*, *::before, *::after {
    box-sizing: border-box;
}
```
- Only put `margin: 0` on `body`.
- It's not bad to use `px` on `margin` and `padding`!
- However, it's better to use `rem` on `font-size`.

## Day 08 - Flexbox, `gap`, `.col + .col`
### Flexbox
- If you want flex items to take up the same width: use `width: 100%`
``` css
.col {
  width: 100%;
}
```
- With this, even an empty flex item will take up the same width as others.

### Using `gap`
- `gap` is an easy way to put spaces around flex items.
- Can be thought of as an alternative of using the `nth child` stuff. 
``` css
.col {
    gap: 100px;
}
```
- Say you have three `col`, the code above will put a `100px` gap between the first & second and second & third columns.  

### Using `.col + .col`
- This selects all `col` that are preceded by another `col`.
- Also an alternative for the `nth child` stuff.
``` css
.col + .col {
    margin-left: 30px;
}
```
- Say we have three `col` again, the code above will only select the second and third `col` because the first column is not preceded by a `col`.
- Therefore, only the second and third `col` will have a `margin-left` of `30px`.

## Days 09 & 10
- The use of `justify-content: space-between;` to create space between flex items.
- By default, `flex` items take up the height of the tallest element in the flex container. So, if you want an `img` to take up the same height as other flex items, do not put it inside a `div`. Otherwise, place it inside a `div`.

- The height of `some-img` will be its actual height.
``` html
    <div class="row">
        <div class="col" id="col-1">...</div>
        <div class="col" id="col-2">
            <img src="/some_image.jpg" id="some-img">
        </div>
    </div>
```
- The height of of `some-img` will adjust according to the height of `col-1`.
``` html
    <div class="row">
        <div class="col" id="col-1">...</div>
        <img src="/some_image.jpg">
    </div>
```

### Using `max-width` for images
- This is to avoid side scrolling, especially on small screens, wherein the actual `width` of an `img` is greater than the current screen width.
``` css
img {
    max-width: 100%;
}
```
## Day 11 - Using flexbox for navigation
- To align `li` items in a single line, you can simply use `display:flex` on `ul`.
``` css
ul {
  display: flex;
}
```
- This is an alternative for setting `display: inline-block` for each `li`.

## Day 12 - `flex-grow`, `flex-shrink`, and `auto` margin
### Using `auto` on `margin
- Using `margin-right: auto` on one of the `nav__item` in `nav__list--primary` will push `nav__list--secondary` to the right of the container.
```html
<nav>
  <ul class="nav__list nav__list--primary">
      <li class="nav__item"><a href="" class="nav__link">Home</a></li>
      <li class="nav__item"><a href="" class="nav__link">About</a></li>
      <li class="nav__item nav__item--push-right"><a href="" class="nav__link">Contact</a></li>
  </ul>
  <ul class="nav__list nav__list--secondary">
    <li class="nav__item"><a href="" class="nav__link">Sign in</a></li>
    <li class="nav__item"><a href="" class="nav__link nav__link--button">Sign up</a></li>
  </ul>
</nav>
```
```css
.nav__item--push-right{
    margin-right: auto;
}
```
- Using `margin: 0 auto` will horizontally center elements.
```css
.nav__list--primary{
    margin: 0 auto;
}
```

## Day 15 - Media Queries
- The use of `min-width` and `max-width`.
### Switching from `display:flex` to `display:block`
- One way to make things to just stack up on smaller screens especially `flex` items that are originally divided into columns on larger screens.
- Better approach instead of changing from `flex-direction: row` to `flex-direction:column`.
- Just make sure that you set the `width` of the elements to `100%`.
``` css
@media(max-width: 600px){

    .row{
        display: block;
    }

    .hero__text,
    .hero__img,
    .left-text,
    .right-text{
        width: 100%;
    }
}
```
- In the code above, `hero__text`, `hero__img`, `left-text`, and `right-text` are all originally `flex` items. However, since `row` has been set to `display:block`, they become block-level elements on `600px` screens.
- Their `width` has been set to `100%` because on larger screens, a different `width` that is only compatible for `display:flex` has also been set. 

### Breakpoints
- [The 100% correct way to do CSS breakpoints by Freecodecamp.](https://www.freecodecamp.org/news/the-100-correct-way-to-do-css-breakpoints-88d6a5ba1862/) 
- The tl;dr of the article: Use `600px`, `900px`, `1200px`, and `1800px` if you plan on giving the giant-monitor people something special. 

## Day 17 - The `meta` `viewport` tag
- Should be present in your `HTML` code for the media queries to work.
``` html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
