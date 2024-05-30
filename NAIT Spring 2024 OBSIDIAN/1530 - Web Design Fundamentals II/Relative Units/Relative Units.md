```table-of-contents
```
# What are Relative Units?
- Relative units are literally relative
- This means their size can change depending upon what is happening around them (e.g. Desktop to mobile)

## Percentages %
An example of a relative unit is Percent (%)
We might use this for font sizes or widths; in this case it'd be relative to the parent container
```HTML
<div class="container">
	<p> Here's some text</p>
</div>
```
```css
div{
font-size: 30px;
}

p{
font-size: 60%
}
```
>[!What This Means] 
>The \<p>would have a calculated font size of 18 pixels (30x0.6 = 18).

What happens if we use percentages for a width that isn't fixed? 
	We would get a <mark style="background: #ADCCFFA6;"><i>fluid width</i></mark> that changes with the size of its parent.

## Viewport Height (vh) & Viewport Width (vw)
- <span style="font-size:2.5vw; color: purple;">1 vw is 1/100th of the total viewport width</span>
- 1 vh is 1/100th of the total viewport height
>[!info] 
>It is always relative to the viewport size

## Ephemeral Units (em)
An em takes the size of something from a parent element and multiplies it to get a new size.

```html
<div>
	<p> Here's some text.</p>
</div>
```

```css
div{
font-size:20px;
}
p{
font-size:0.5em;
}
```

>[!What This Means]
>Lets say the font size of our \<div> is 20 pixels. The \<p> would have a calculated font-size of 10 pixels (20 x 0.5 = 10).

Using em can be tricky because you will need to keep track of the parent element's size.

## Root Ephemeral Units (rem)
A rem is always relative to the root element (i.e. the body or html).

16px is the default.

```css
html{
font-size: 100%;
}

h1{
font-size: 2.25rem;
}

p{
font-size: 1rem;
}
```
>[!What This Means]
>If \<html>'s font size is 100%, then it will be rendered as 16px by the browser (because this is the default size). Therefore \<h1> will be rendered as 36px (16 x 2.25 = 36). \<p> will be rendered as 16px (16 * 1 = 16)

# An Old Hack
## Define Your Own Typographic Scale
![[Pasted image 20240521193854.png]]
## Calc() function in CSS
![[Pasted image 20240521193937.png]]

