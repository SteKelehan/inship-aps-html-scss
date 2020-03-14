# CSS Bad to Okay

## The 3 Pillars of website

#### Responsive design

- Work on all screen sizes

#### Maintainable and scalable code

- Clean, reusable and organized

#### Web performance

- Make as little as HTTP req as possible
- Less images
- Compres images
- Compress code
- CSS preprocessor



## General Setup

You want to set universal setting to the webpage as each browesr has default setting. The symble for this is \*.

Generaly you will want to have the following settings

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

- box-sizing: border-box is so the padding and margin do not get added to the size of elements

All classes will inherit those properies

We allso want to sent univeral properies for the body. You could include these in the \* too. But it is good pratice to put them in the body universal selecter that all the child classes will inherit. These are nornmal anything to do with text. Example below:

```css
body {
  font-family: 'Lato', sans-serif;
  font-weight: 400;
  font-weight: 16px;
  line-height: 1.7;
  color: #777;
}
```

In order to change the rem unit you need to add it in the html class like below:

```css
html {
  font-size: 10px;
}
```

You should then use rem for everything. This way you can then change the font-size relotively when the screen size chanegs by change ing the html default font-size

## Basics

#### Height and Width's

- When you see vh or vw. This means view height and view width. It will always be x% of the viewable height or with
- When you spesify the height of an img/box anything it will auto chose the width for you

#### Background

```css
.header {
  height: 95vh;
  background-image: linear-gradient(to right bottom, #7ed56fc9, #28b485d0),
    url(../img/hero.jpg);
  background-size: cover;
  background-position: top;
}
```

In the above there is a lot going on.

background-image is where we put in an image we are going to be using with text overlaying it.

The linear-gradient:

- This is givening the img a color over it that gose from one color to the other slowly and naturaly.
- The "to right bottom" is telling the linear-gradiant where to do the proform the linear-gradiant
- The background-size: cover is just telling it to cover the size of the class
- Finally the background-postion: top is saying that when the screen changes size that the top of the imag will always stay at top of the webpage.

##### Cool tools for backgound

There is a function taht allows you to make shapes out of the backgound images it is called clip-path

```css
clip-path: polygon(x y, x y, x y, x y);
```

[Make quick shapes here](https://bennettfeely.com/clippy/)

### Positioning

Position relative and absolute.

- If you set a class to be postion absolute it will be a free agent and the top, left etc. that you set it will be from the top conor of the webpage.
- But if there is a parent class (this being in the html or css) and that parent has a position relative. The coordiants you define in the chile class will be from the top left coner of that element

```css
.parent {
  position: relative;
}
```

```css
.child {
  top: 40px;
  left: 40px;
  position: absolute;
}
```

In the example below the you can see that the class-A is the parent of class-B

```html
<div class="class-A">
  <img src="img/logo-white.png" alt="Logo" class="class-B" />
</div>
```

- If you wanted to postion a box in the center of a box you would need to do the following:

```css
.text-box {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

- There would be a parent element that has posisition: rel. You then but the text-box in the center of that parent element. But the element's top left hand conor is in the center. This you need to transform the box by -50% ( it is 50% as this is with refrence to the text-box )

###### Display boxs

- These occupy 100% of the with and the creat line breaks

```css
.heading-primary-main {
  display: block;
}
```

### Text

#### Headers

- **NOTE :** The h1 is the most importamnt header in the website. This is what google will use to determain what kind of website it is. It will contribute hugely to google searches

#### Span

This is used to syle text that needs to say on the same line. Div's will break the text up onto new lines etc.

#### Go to know functions

- text-transform: uppercase; (make all the text uppercase)
- letter-spacing: put space between each letter

## Anamation

### @Keyframs

You can used these to make css anamitions.

The way keyframes works is you define what you want to happen at each stage. You do this with %.

So what happens at 0% then 7% then 80% then finally 100%. It will then transistion between these states as smoothly as possible

The broweser is only optimised to use two ways to anamate an element

- opacity
- transform

You can do a lot with just these two.

There is a example below:

```css
.element-you-are-animatin {
  animation-name: moveInLeft;
  animation-duration: 3s;
}

@keyframes moveInLeft {
  0% {
    opacity: 0;
    transform: translate(-100px);
  }

  100% {
    opacity: 1;
    transform: translate(0);
  }
}
```

This will on page load start from -100px from its static spot and not been visable and then slowly be become visable and move into it staic postion.

In the class of the element you are animating you need to add two things.

1. animation-name -> this is the name of the animation
2. animation-duration -> this is the lenght of time it will take to preform the animation
3. animation-fill-mode -> property specifies a style for the element when the animation is not playing

##### Other Keyframs functions

1. animation-delay -> This gives a delay when the animation starts
2. animation-itteration-count -> How many times you want the animation happen
3. animation-timing-function -> This is a function that allows you to change when the animation speeds up and slows down.

- **NOTE**

This

```css
.class-name {
  animation-name: moveInLeft;
  animation-duration: 1s;
  animation-timing-function: ease-out;
}
```

is the same as this

```css
.class-name {
  animation: moveInLeft 1s ease-out;
}
```

- **NOTE**

If you get a shaky animation you need to use the follow in a parent class:

```css
.parent-class {
  backface-visibility: hidden;
}
```

[Here](https://developer.mozilla.org/en-US/docs/Web/CSS/transform) is a link to mutliple types of transformations

### Transistion

This is yet another way to have animations. This can be used in conjuntion witrh pseudo element (explained in next sestion)

- You have to set the transisiton functoin in the inital class. You spesify what of the element you want to animate and the duration.
- You then can use the transform function to animate

```css
.class {
  transition: all 0.2s;
}

.class:hover {
  transform: translateY(-3px);
}

.class:active {
  transform: translateY(1px);
}
```

This element will move up when you hover over it and the move down with you click it.

##### Transform functions

1. translate
2. scale

## Pseudo elements and classes

A pseudo class is defining a special state of a class.

For example

```css
.class:hover {
  color: white;
}
```

The pseduo element defines what the class will do when in that state. So when the mouse is hoving over the element it iwll change the text to white.

Pseudo classes:

1. :hover
2. :link (when it is a link do x)
3. :visisted (when you click the link to x)
4. :active (this is when you click an element do x)
5. ::after
6. ::before

The ::after and ::before selectors simply put content specified before or after the content of the class its attached too.

```css
.class{
    color: black;
    font-size: 10px;
}

.class::before{
    content: "hi";
    color: blue;
}

.class::after{
    content: "hello"
    color:yellow;
}

```

It will look like the following:

<span style="color:blue">hi</span> This is the text that was in the class class
<span style="color:yellow">hello</span>

These two can be used ot make some powerfull animations too.

You can make a copy of the element put it behind it and hide it with a z index of less than it and do some cool animatins
