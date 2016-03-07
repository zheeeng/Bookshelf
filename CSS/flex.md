# Flex layout

*Origin Link: <https://www.w3.org/TR/css-flexbox-1/#propdef-justify-content>*

**Note:** `::first-line`, `::first-letter` and `column-*` have no effect on flex container; `float`, `clear` and `vertical-align` have no effect on flex item. 

### Flex Elements

1. flex container
    * main axis 
    * main start
    * main end
    * cross aixs
    * cross start 
    * cross end
2. flex item
    * main size
    * cross size

### Flex Container

#### Display

```css
.flex-container {
    display: -webkit-flex | -webkit-inline-flex; /* for safari */
    display: flex | inline-flex;
}
```

#### Flex Container Properties

```css

.flex-container {
    flex-direction: row | row-reverse | column | column-reverse;
    flex-wrap: nowrap | wrap | wrap-reverse;
    /* align along main axis: */
    justify-content: flex-start | flex-end | center | space-between | space-around;
    /* cross axis alignment: */
    align-items: flex-start | flex-end | center | baseline | stretch;
    /* flex container’s lines aIgnment: */
    align-content: flex-start | flex-end | center | space-between | space-around | stretch;
}

/* shorthand for setting 'flex-direction' and 'flex-wrap' */
.flex-container {
    flex-flow: <flex-direction> || <flex-wrap>;
}

```
For safari compatibility, add prefix '-webkit-' to flex proerties.

### Flex item

```css

.flex-item {
    order: <integer>;
    flex-grow: <number>; /* default: 0 */
    flex-shrink: <number>; /* default: 1 */
    flex-basis: <length> | auto; /* default: auto */
    /* cross axis alignment: */
    align-self: auto | flex-start | flex-end | center | baseline | stretch;
}

.flex-item {
    /*
     'none' expands to '0 0 auto';
     'auto' expands to '1 1 auto';
    */

    flex: none | auto | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ];
}

```

