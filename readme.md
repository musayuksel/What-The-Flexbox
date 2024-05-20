# What The Flexbox?!

<img src="https://flexbox.io/images/WTF/share.png" alt="what is flex box" width="400"/>

Exercises for the "What The Flexbox?!" video course. Videos available at <http://flexbox.io>

## Community What The Flexbox Content

Feel free to submit a PR adding a link to your own recaps, guides or reviews!

My [gh-page](https://herminiotorres.github.io/whattheflexbox) by [@herminiotorres](https://twitter.com/herminiotorres)

## Properties for the Parent(flex container)


- **flex-direction:**
  ```css
  .container {
    flex-direction: row | row-reverse | column | column-reverse;
  }
  ```

  - *row* (default): left to right in ltr; right to left in rtl
  - *row-reverse:* right to left in ltr; left to right in rtl
  - *column*: same as row but top to bottom
  - *column-reverse*: same as row-reverse but bottom to top

- **flex-wrap:**
  ```css
  .container {
    flex-wrap: nowrap | wrap | wrap-reverse;
  }
  ```

  - *nowrap:* (default): all flex items will be on one line
  - *wrap:* flex items will wrap onto multiple lines, from top to bottom.
  - *wrap-reverse:* flex items will wrap onto multiple lines from bottom to top.

- **flex-flow:** shorthand for the flex-direction and flex-wrap 
  - default: *row nowrap*.
  ```css
  .container {
      flex-flow: column wrap;
  }
  ```
- **justify-content:**
  ```css
  .container {
    justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe;
  }
  ```

  - *flex-start* (default): items are packed toward the start of the flex-direction.
  - *flex-end:* items are packed toward the end of the flex-direction.
  - *space-between:* items are evenly distributed in the line; *first* item is on the start line, *last* item on the end line
  - *space-around:* items are evenly distributed in the line with equal space around them.
    - Note: `1xSpace Element 1xSpace 1xSpace Element` will repeat so the first and last element will be close to their edges
  - *space-evenly:* items are distributed so that the spacing between *any two items* (and the space to the edges) is equal.
  - *center:* items are centered along the line
  - *start*: items are packed toward the start of the *writing-mode* direction.
  - *end*: items are packed toward the end of the *writing-mode* direction.
  - *left/right*: items are packed toward *left/right* edge of the container, unless that doesn’t make sense with the *flex-direction*, then it behaves like *start/end*
  - ***safe and unsafe:*** additional keywords you can pair,  using safe ensures that however you do this type of positioning, you can’t push an element such that it renders off-screen (e.g. off the top) in such a way the content can’t be scrolled too (called “data loss”).


- **align-items:**
  ```css
  .container {
    align-items: stretch | flex-start | flex-end | center | baseline | first baseline | last baseline | start | end | self-start | self-end + ... safe | unsafe;
  }
  ```

  - *stretch* (default): stretch to fill the container.
  - *flex-start / start / self-start:* items are placed at the start of the cross axis. 
  - *flex-end / end / self-end:* items are placed at the end of the cross axis.
  - *center:* items are centered in the cross-axis
  - *baseline:* items are aligned such as their baselines align



- **align-content:**
  ```css
  .container {
    align-content: flex-start | flex-end | center | space-between | space-around | space-evenly | stretch | start | end | baseline | first baseline | last baseline + ... safe | unsafe;
  }
  ```
***Note:*** This property only takes effect on **multi-line** flexible containers, where flex-wrap is set to either `wrap` or `wrap-reverse`. A single-line flexible container (i.e. where flex-wrap is set to its default value, no-wrap) **will not** reflect align-content.

  - *normal* (default): tems are packed in their default position as if no value was set.
  - *flex-start / start:* items packed to the start of the container.  
  - *flex-end / end:* items packed to the end of the container. 
  - *center:* items centered in the container
  - *stretch/space-between/space-around/space-evenly:* items are distributed such as evenly etc



- **gap, row-gap, column-gap:**
  ```css
  .container {
    display: flex;
    <!-- other styles -->
    gap: 10px;
    gap: 10px 20px; /* row-gap column gap */
    row-gap: 10px;
    column-gap: 20px;
  }

  ```
***Note:*** The ***gap*** property explicitly controls the space between flex items. It applies that spacing only between items **not on the outer edges.**

The behavior could be thought of as a minimum gutter, as if the gutter is bigger somehow (because of something like justify-content: space-between;) then the gap will only take effect if that space would end up smaller.


## Properties for the Children(flex items)

- **order:**
  ```css
  .item {
    order: 5; /* Default is 0*/
  }
  ```

  - By default, flex items are laid out in the source order.
  - We can use *negative* number to push items to the beginning of the container


- **flex-grow:**
  ```css
  .box {
    flex-grow: 1; /* Default is 0*/
  }
  .box2 {
    flex-grow: 2; /* Default is 0*/
  }
  ```

  - If all items have `flex-grow` set to **1**, the remaining space in the container will be distributed equally to* all children*.
  - If one of the children-`box2`  has a value of **2**, that one would take up **twice** as much of the space as either one of the others (or it will try, at least).(`1fr 2fr`)



- **flex-shrink:**
  ```css
  .box2 {
    flex-shrink: 2; /* Default is 1*/
  }
  ```

  - This defines the ability for a flex item to shrink if necessary.
  - `.box2` will shrink 2 times faster than others
  - Negative numbers are invalid.


- **flex-basis:**
  ```css
  .box2 {
    flex-basis: auto; /* Default is auto*/
  }
  ```

  - This defines the *default* size of an element before the remaining space is distributed. It can be a length (e.g. 20%, 5rem, etc.) or a keyword. 
  - *content:* size it based on the item’s content


- **flex:**
  ```css
  .box {
  flex: 1; /* Default is: flex: 0 1 auto*/
  }

  .box3 {
  flex: 2;
  } 
  ```
  - Most popular one is `flex:1`
  - In the example all `.box`s same size, but `.box2` 2 times bigger then others
  - The shorthand for `flex-grow`, `flex-shrink` and `flex-basis `combined.
  - The **second** and **third** parameters (flex-shrink and flex-basis) are optional. 

```css
  .box {
    flex: 1 1 300px;
  }
  .box3 {
    flex: 5 1 100px;
  }
```
  - `.box3` will grow 5 times faster than others. Default base size for `.boz3` will be `100px` 


- **align-self:**
  ```css
  .box2 {
     align-self: center;
  }
  ```

  - Override the default/given alignment
  -  Same values with *align-items*: `auto` | `flex-start` | `flex-end` | `center` | `baseline` | `stretch`;

