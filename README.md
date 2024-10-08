# @nnexCSS 

AnnexCSS is a lightweight single-file pure CSS animation library.

NOTE: deprecated and removed from npm

You can easily add animations to your JSX or markup just like any regular CSS class  

```HTML

<div className="@fadeIn"> I love potato </div>

```

You can extend functionality by adding utility classes 


```HTML

<div className="@fadeIn flex">
  <div className="@fadeIn @delay-1s flex-none ...">
    01 Potato
  </div>
  <div className="@fadeIn @delay-2s flex-1 w-64 ...">
    02 Potato
  </div>
  <div className="@fadeIn @delay-3s flex-1 w-32 ...">
    03 Potato
  </div>
</div>

```

<br/>

|      Classes      |                    |                     |                      |
| ----------------- | ------------------ | ------------------- | -------------------- |
| `@bounce`          | `@flash`            | `@pulse`             | `@rollIn`             |
| `@shake`           | `@headShake`        | `@swing`             | `@rollOut`            |
| `@wobble`          | `@tada`             | `@bounceIn`          | `@bounceInDown`       |
| `@bounceInLeft`    | `@bounceInRight`    | `@bounceInUp`        | `@bounceOut`          |
| `@bounceOutDown`   | `@bounceOutLeft`    | `@bounceOutRight`    | `@bounceOutUp`        |
| `@fadeIn`          | `@fadeInDown`       | `@fadeInDownBig`     | `@fadeInLeft`         |
| `@fadeInLeftBig`   | `@fadeInRight`      | `@fadeInRightBig`    | `@fadeInUp`           |
| `@fadeInUpBig`     | `@fadeOut`          | `@fadeOutDown`       | `@fadeOutDownBig`     |
| `@fadeOutLeft`     | `@fadeOutLeftBig`   | `@fadeOutRight`      | `@fadeOutRightBig`    |
| `@fadeOutUp`       | `@fadeOutUpBig`     | `@flipInX`           | `@flipInY`            |
| `@flipOutX`        | `@flipOutY`         | `@slideInUp`         | `@slideOutUp`         |
| `@rotateIn`        | `@rotateInDownLeft` | `@rotateInDownRight` | `@rotateInUpLeft`     |
| `@rotateInUpRight` | `@rotateOut`        | `@rotateOutDownLeft` | `@rotateOutDownRight` |
| `@rotateOutUpLeft` | `@rotateOutUpRight` | `@zoomOutUp`         | `@zoomOut`            |
| `@zoomIn`          | `@zoomInDown`       | `@zoomInUp`          | `@zoomOutRight`       |
| `@zoomInLeft`      | `@zoomInRigh`       | `@slideOutRight`     | `@slideOutLeft`       |  
| `@zoomOutDown`     | `@zoomOutLeft`      | `@slideInRight`      | `@slideOutDown`       |
| `@slideInDown`     | `@slideInLeft`      |  


<br/> 


|    Utilities      |                    |                     |                      |
| ----------------- | ------------------ | ------------------- | -------------------- |
| `@infinite`        | `@reapeat-1`        | `@repeat-2`          | `@repeat-3`         |
| `@delay-1s`        | `@delay-2s`         | `@delay-3s`          | `@delay-4s`         |
| `@delay-5s`        | `@faster`           | `@fast`              | `@slow`             |
| `@slower`          |

<br/>



So how does it work? AnnexCSS first creates variables in :root to reuse as basic properties. 


```CSS

:root {

    --animate-repeat: 1;
    --animate-duration: 1s;
    --animate-delay: 1s;

}

```

It then wraps all elements (*) with required core properties for individual classes to function properly. All classes use this wrapper when applied. This is a core feature unique to AnnexCSS.

```CSS
* {
  
    animation-duration: 1s;
    animation-duration: var(--animate-duration);
    animation-fill-mode: both;
    -webkit-animation-fill-mode: both;
    -webkit-animation-duration: var(--animate-duration);
    -webkit-animation-duration: 1s;

}
```
 
In regards to browser compatibility AnnexCSS focuses entirely on webkit. Postcss with autoprefixer can assist you if you need to expand cross-compatibility. Classes typically look like this:

```CSS
@-webkit-keyframes fadeIn {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}
@keyframes fadeIn {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}
.\@fadeIn {
  -webkit-animation-name: fadeIn;
  animation-name: fadeIn;
}

```

You can call the @keyframes directly in any class. Just make sure to declare the duration too.

```CSS

.bounceHover:hover {

  animation: bounce; 
  animation-duration: 2s; 

}

```

And you can change variables to customize your animations. Make sure you use a backslash to escape the @ when cascading over the animation classes. All AnnexCSS classes use @ as a prefix.

```CSS

.\@fadeIn {

  --animate-duration: 10s;
  
}

```

# About

This library was originally compiled using a custom animate.css build so you may take notice of the simliar class names. Many of the "uncommon" classes were removed to simplify the class set and reduce build size as much as possible.

Originally I wanted to use animate.css itself but it's getting a bit older now and had unneeded overhead for my use case. 

There is one major core difference outside of the postcss scripts and size. AnnexCSS wraps all elements with required properties instead of individually applying them. This allows for cleaner markup. Instead of animate__animated animate__fadeIn just for one animation, you just need @fadeIn etc. 

Using with PurgeCSS is recommended.
