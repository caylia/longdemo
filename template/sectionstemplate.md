# Template
For some scroll animations with animation-timeline scroll() or view(), they will only work on supported browser like Google Chrome (from version 115), Edge Explorer (from version 115), and Opera (from version 101), as for now Firefox and Safari has no support for these kind of animations yet. 


## Section10 Template
This section has a background change animation as you scroll the section. Works well if there are a lot of contents (paragraphs, images) in the section, as that will increase the height of this template and there will be more scrolling in this section. 

The template has a scroll animation with animation-timeline view(). When the section is in the viewport, as you scroll the background-image will change like a still animation (displaying images as frames in frame-by frame technique). If you scroll down, the next frame of the animation will show on the background and if you scroll up again, the previous frame will show on the background. 

In this section the headers, paragraphs and images will be placed under each other in a sequence starting from the first element to the last element.


![image of how section10 template can look like on the screen](section10all.jpg "image of section10")

The image shows what the section look like while scrolling down the section from a to b to c and then to d. 



### HTML Structure
The HTML structure for this section looks like this:


```
<div class="section" id="section10">
    <div class="background"></div>
    <div class="container"></div>
</div>

```


This section will need a div tag for section with a class "section" and a unique id, example "section10". Inside the div tag for this section, it needs a div tag for the background-image with div class "background", and a div tag for a container that will consists of the content of section. 


The content of the section like headers (<h4>), paragraphs (<p>), and figures/images (<figure>) will be inside the div tag with class name container, like for example:


```
<div class="section" id="section10">
    <div class="background"></div>
    <div class="container">
        <h4>This is a Header</h4>
        <p>This is a short paragraph</p>
        <figure><img src="image1.jpg"></figure>
    </div>
</div>

```


### CSS properties

#### #section10

The properties of section10 in the CSS template: 


```
#section10{
    min-height: 200vh;
    width: 100%;
    position: relative;
    align-items: center;
    padding: 0;
    */
}
```


The property min-height: 200vh; ensures this section will have a minimum height of 200vh (which is twice the height of viewport), and the height will increase if the contents of the section require more space. 



#### #section10 .background

In the section10 div tag with class "background" will be defined as #section10 .background in CSS and has these CSS properties:


```
#section10 .background{
    width: 100%;
    height: 100vh;
    position: sticky;
    top: 0;
    z-index: 1;
    background-image: url('1.jpg');
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
    animation: BackgroundImageChange linear;
    animation-timeline: view(100% 20%);
}
```


 The height is set to 100vh because we want the background-images to cover the whole viewport. The CSS property *position: sticky*, sticks the container to the section so it is always visible in the section when you are scrolling through this section. In order for the container to have sticky position that covers the whole viewport of the section, it is needed to specify the *top* property, it is set top: 0;, so container starts sticking to the top of viewport when top of it reaches the top of the viewport. 

 The property z-index specifies the stack level priority of the element in the local stacking context. The .background has z-index: 1 while .container has z-index: 2, so .container has a higher stacking priority than .background, therefor .container will be stacked on top of .background. 


The background-* properties are for the background-images in the animation BackgroundImageChange. The background-image will centered, cover the whole viewport (may stretch or cut some part of the image). 

The animation with name *BackgroundImageChange* has animation-timing-function linear, meaning it animate the frames at an even speed. 

Animation-timeline has the function view(), with parameters view(100% 20%), the first value 100% and the second value 20% cause the animation to start from 10% from the bottom of the viewport and finising at 100% from the top when scrolling down section10. 


##### Animation BackgroundImageChange

*BackgroundImageChange* in CSS are presented in *@keyframes BackgroundImageChange* :

```
@keyframes BackgroundImageChange{
    0%{
        background-image: url('')
    }
    10%{
        background-image: url('')
    }
    20% {
        background-image: url('')
    }
    30% {
        background-image: url('')
    }
    40% {
        background-image: url('')
    }
    50% {
        background-image: url('')
    }
    60% {
        background-image: url('')
    }
    70% {
        background-image: url('')
    }
    80% {
        background-image: url('')
    }
    90% {
        background-image: url('')
    }
    100% {
        background-image: url('')
    }
}
```

The % before a CSS style, is the percentage of the time through the animation sequence at which a keyframe should take place. At 0% is the start of the animation and at 100% is the end of the animation. 

The *BackgroundImageChange* has the sequence divided into 11 parts in percentages (0%, 10%, 20%, ..., 100%) and each has a CSS style *background-image: url('')* so it is possible to have 11 background-images. It is also possible to adjust *BackgroundImageChange* if there is more or less background-image frames needed by changing the percentage sequence. 

For example if only five images is needed, so less frames is needed, can modify the *BackgroundImageChange* to:


```
@keyframes BackgroundImageChange{
    0%{
        background-image: url('image1.jpg')
    }
    25% {
        background-image: url('image2.jpg')
    }
    50% {
        background-image: url('image3.jpg')
    }
    75% {
        background-image: url('image4.jpg')
    }
    100% {
        background-image: url('image5.jpg')
    }
}
```


#### #section10 .container
The div with class "container" inside section10 has CSS properties:

```
#section10 .container{
    position: relative;
    z-index: 2;
    padding: 2rem;
    margin-top: -100vh;
}

```


The container has width 100% that will cover the size of the section it is inside in.

The z-index: 2 makes sure that the .container will be places on top of the .background, so the content of the container will be visible and not hidden. 

There is a margin-top: -100vh to counter and hide the space that is created from the div class "background" that has height: 100vh. This can be adjusted if there is a wish for more space between when the section starts before the contents shows up while scrolling. Example margin-top: -50vh for the content to show on the bottom half of the viewport, or remove the margin-top property totally if the content should come into view after scrolling 100vh down the section. 


#### Text, headers and paragraphs formatting

The HTMl text formats like ```<p>``` defining a paragraph, and ```<h1>, <h2>, <h3>, <h4>, <h5>``` defining headers in different font-sizes, where h1 has the largest font-size and h5 has the smallest font-size out of these headers by default. These sizes can be adjusted to one's need. 


```
#section10 p {
    font-size: 20px;
    color: pink;
    font-family: Arial;
}

#section10 h4 {
    font-size: 40px;
    color: lightblue;
    font-family: Arial;
    text-shadow: -3px -2px 0px #ffffff;
}

#section10 h5 {
    font-size: 30px;
    color: lightgreen;
    font-family: Arial;
    text-shadow: -3px -2px 0px #ffffff;
}
```

The paragraph and headers have their own CSS selectors. The paragraphs are here set to have smaller font-size than the headers h4, h5 and have font color pink, and font family Arial. All of these CSS properties can be modified to one's need, example smaller font-size: 15px, and blue color on the font color: blue; or can also use rgb color code. 

For h4 and h5, the same properties can also be modified as one wish. In addition there is another CSS property, text-shadow, this property adds shadow to the text. There are set four values to the text-shadow, the first parameter -3px is the h-shadow which is the position of horizontal shadow. The second parameter is -2px is the v-shadow,the position of vertical shadow. The third parameter is set as 0 here is the blur-radius, this parameter is optional and can be dropped if no blur-radius is needed. The last parameter is the color of the shadow. All these four parameters can be adjusted to be the headers to look for three-dimentional. If text-shadow is not needed, this property can be dropped from the selector. 



#### Figures and Images

The images in the section will be inside the ```<figure>``` tag and in this section has these CSS properties:


```
#section10 figure{
    max-width: 100%;
    height: auto;
}

#section10 figure img{
    max-width: 100%;
    height: auto;
    border-radius: 10px;
    border: 10px solid white;
    border-bottom-width: 50px;
    box-shadow: 10px 10px lightgrey;
}
```


In figure, the figure block will have max-width: 100% so it will cover the .container area, and the height will be auto set based on the max-width. 

The images in this section will have a polaroid looking picture with rounded corners frame. 
The images ```img``` inside the figure tag has also max-width: 100% so it will cover the width of the figure. There is a border-radius property that rounds the edges of the border, it is set border-radius: 10px, which gives slightly rounded edges. If there is a wish for even rounder edges, just increase the border-radius to a higher number of px, example border-radius: 30px. It is possible to make the image more circular by changing radius to border-radius: 50%. The border-radius can be removed if rounded egdes is not needed, but would rather have sharp edges. 


#### Position of the content of the section

For the content of the section such as figures, paragraphs lists, headers to be positioned in the middle, these CSS properties are set:


```
#section10 figure, #section10 p, #section10 li, #section10 h4, #section10 h5{
    position: relative;
    margin: 25px;
    margin-left: 25%;
    margin-right: 25%;
}

```

The margin around an element is 25px, to have more margin around an element can increase to exmaple margin: 35px, or to have less margin by decrease to for example margin: 10px. 

The combination of margin-left and margin-right, both set to 25%, causes the contents to be centered horizontally of the viewport. 

The content can be positionted to the left side by setting the margin-left and margin-right to:

```
    margin-left: 0%;
    margin-right: 50%;

```

Or for the content to be on the right side by setting them to:
```
    margin-left: 50%;
    margin-right: 0%;

```

It is fully possible to adjust the margins values as one wish other than the mentioned values. 

