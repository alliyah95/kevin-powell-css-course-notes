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
```
.container{
   width: 80%;
   max-width: 800px;
}
```
- The code above means that, for all screen sizes, the `width` of `container` should be `80%` of its parent. However, when the value of `80%` in `px` is equal or greater than `80`, the `width` should stop adjusting from there.

## Days 04 - 07 - More about the previous topics
- The use of `box-sizing: border-box`
```
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
```
.col {
  width: 100%;
}
```
- With this, even an empty flex item will take up the same width as others.

### Using `gap`
- `gap` is an easy way to put spaces around flex items.
- Can be thought of as an alternative of using the `nth child` stuff. 
```
.col {
    gap: 100px;
}
```
- Say you have three `col`, the code above will put a `100px` gap between the first & second and second & third columns.  

### Using `.col + .col`
- This selects all `col` that are preceded by another `col`.
- Also an alternative for the `nth child` stuff.
```
.col + .col {
    margin-left: 30px;
}
```
- Say we have three `col` again, the code above will only select the second and third `col` because the first column is not preceded by a `col`.
- Therefore, only the second and third `col` will have a `margin-left` of `30px`.
