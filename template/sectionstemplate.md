# Template
For some scroll animations with animation-timeline scroll() or view(), they will only work on supported browser like Google Chrome (from version 115), Edge Explorer (from version 115), and Opera (from version 101), as for now Firefox and Safari has no support for these kind of animations. 



## Section10 Template
This section has a background change animation as you scroll the section. Works well if there are a lot of contents (paragraphs, images) in the section, as that will increase the height of this template and there will be more scrolling in this section. 

The template has a scroll animation with animation-timeline view(). When the section is in the viewport, as you scroll the background-image will change like a still animation (displaying images as frames in frame-by frame technique). If you scroll down, the next frame of the animation will show on the background and if you scroll up again, the previous frame will show on the background. 

In this section the headers, paragraphs and images will be placed under each other in a sequence starting from the first element. 

The properties of section10 in the CSS template: 


```
#section10{
    min-height: 200vh;
    width: 100%;
    align-items: center;
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
    background-attachment: fixed;
    animation: BackgroundImageChange linear;
    animation-timeline: view();
}

```

The property min-height: 200vh; ensures this section will have a minimum height of 200vh (which is twice the height of viewport), and the height will increase if the contents of the section require more space. 

The background-* properties are for the background-images in the animation BackgroundImageChange. The background-image will centered, cover the whole viewport (may stretch or cut some part of the image), and be fixed to the section's background. 

The animation with name *BackgroundImageChange* has animation-timing-function linear, meaning it animates at at even speed. 


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

The *BackgroundImageChange* has the sequence divided into 11 parts in percentages (0%, 10%, 20%, ... 100%) and each has a CSS style *background-image: url('')* so it is possible to have 11 background-images. It is also possible to adjust *BackgroundImageChange* if there is more or less background-image frames needed by changing the percentage sequence. For example if only five images is needed, so less frames is needed,  can modify the *BackgroundImageChange* to:

```
@keyframes BackgroundImageChange{
    0%{
        background-image: url('')
    }
    25% {
        background-image: url('')
    }
    50% {
        background-image: url('')
    }
    75% {
        background-image: url('')
    }
    100% {
        background-image: url('')
    }
}
```












