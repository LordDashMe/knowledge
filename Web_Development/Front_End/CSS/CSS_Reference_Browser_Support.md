# CSS Referece Browser Support

## FLEX

```css
display: -webkit-box;  /* OLD - iOS 6-, Safari 3.1-6 */
display: -moz-box;     /* OLD - Firefox 19- (buggy but mostly works) */
display: -ms-flexbox;  /* TWEENER - IE 10 */
display: -webkit-flex; /* NEW - Chrome */
display: flex;         /* NEW, Spec - Opera 12.1, Firefox 20+ */
```

## FLEX-GROW

```css
-webkit-flex-grow: 1;
-moz-flex-grow: 1;
-ms-flex-grow: 1;
flex-grow: 1;
```

## FLEX-WRAP

```css
-webkit-flex-wrap: wrap;
-moz-flex-wrap: wrap;
-ms-flex-wrap: wrap;
flex-wrap: wrap;
```

## FLEX-DIRECTION

```css
-webkit-flex-direction: column;
-moz-flex-direction: column;
-ms-flex-direction: column;
flex-direction: column;
```

## FLEX-FLOW

```css
-webkit-flex-flow: column;
-moz-flex-flow: column;
-ms-flex-flow: column;
flex-flow: column;
```

## JUSTIFY CONTENT

```css
-webkit-justify-content: center;
-moz-justify-content: center;
-ms-justify-content: center;
justify-content: center;
```

## ORDER

```css
-webkit-order: 1;
-moz-order: 1;
-ms-order: 1;
order: 1;
```

## TRANSFORM

```css
-webkit-transform: translate3d(0, -2.5rem, 0);
-moz-transform: translate3d(0, -2.5rem, 0);
-ms-transform: translate3d(0, -2.5rem, 0);
transform: translate3d(0, -2.5rem, 0);
```

## GRADIENT IN CSS

```css
/* IE10 Consumer Preview */
background-image: -ms-linear-gradient(left, #162D67 0%, #00A3EF 100%);
/* Mozilla Firefox */
background-image: -moz-linear-gradient(left, #162D67 0%, #00A3EF 100%);
/* Opera */
background-image: -o-linear-gradient(left, #162D67 0%, #00A3EF 100%);
/* Webkit (Safari/Chrome 10) */
background-image: -webkit-gradient(linear, left, left, color-stop(0, #162D67), color-stop(1, #00A3EF));
/* Webkit (Chrome 11+) */
background-image: -webkit-linear-gradient(left, #162D67 0%, #00A3EF 100%);
/* W3C Markup, IE10 Release Preview */
background-image: linear-gradient(to left, #162D67 0%, #00A3EF 100%);
```
