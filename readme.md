# What The Flexbox?!

<img src="https://flexbox.io/images/WTF/share.png" alt="what is flex box" width="400"/>

Exercises for the "What The Flexbox?!" video course. Videos available at <http://flexbox.io>

## Community What The Flexbox Content

Feel free to submit a PR adding a link to your own recaps, guides or reviews!

My [gh-page](https://herminiotorres.github.io/whattheflexbox) by [@herminiotorres](https://twitter.com/herminiotorres)

## Flex

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
