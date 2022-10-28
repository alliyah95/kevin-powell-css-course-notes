# Notes from Kevin Powell's Conquering Responsive Layouts Course
## Days 01 & 02
- Avoid explicitly setting the `height` of elements.
  - Say you want more whitespace, you can utilize `padding`.
- `em` is relative to the `font-size` of a parent element.
  - It is mostly useful for buttons.
- `rem` is relative to the root `font-size`, or the one set in `html`.
- Use percentages instead of `px` for `width`.

## Day 03
- The use of `width` together with `max-width`.
```
.container{
   width: 80%;
   max-width: 800px;
}
```
- The code above means that, for all screen sizes, the `width` of `container` should be `80%` of its parent. However, when the value of `80%` in `px` is equal or greater than `80`, the `width` should stop adjusting from there.

