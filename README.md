# @nnexCSS 

AnnexCSS is a lightweight single-file pure CSS animation library made for use with Next.js in a TBA front-end framework. It can be used independently with any web framework or project that utilizies webpack.

When minified the entire module takes up <1kb. Should you require only a few basic animations the annex.css file can easily be searched without much effort reducing your CSS overhead even further. Just copy what you need to your global.css 🏴‍☠️

```bash
npm i annexcss
```
```bash
import 'annexcss'
```

You can easily add animations to your JSX or markup just like any regular CSS class  

```HTML

<div className="@fadeIn container"> I love potato </div>

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
<br/>


|    Utilities      |                    |                     |                      |
| ----------------- | ------------------ | ------------------- | -------------------- |
| `@infinite`        | `@reapeat-1`        | `@repeat-2`          | `@repeat-3`         |
| `@delay-1s`        | `@delay-2s`         | `@delay-3s`          | `@delay-4s`         |
| `@delay-5s`        | `@faster`           | `@fast`              | `@slow`             |
| `@slower`          |

<br/>

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

# About

All AnnexCSS classes are prefixed with an @ symbol. This library was originally compiled using a custom animate.css build so you may take notice of the simliar class names. Many of the "uncommon" classes were removed to simplify the class set and reduce build size as much as possible. 

Using the animate.css package to compile annex.css was just a method to prefix and quickly iterate on commonly used CSS animation techniques for an accompanying JS framework. 

Originally I wanted to use animate.css itself or a fork of the project but the project is a bit older now and had unneeded overhead. The current recent versions of Next.js (>9.5.0) make the animate.css postcss scripts a bit redundant.

There is one major core difference outside of the scripts and size. AnnexCSS wraps all elements with required properties instead of individually applying them. This allows for cleaner markup. Instead of animate__animated animate__fadeIn just for one animation, you just need @fadeIn etc. Tree shaking handles anything unused before it even hits the browser. If you have a a completely vanilla project that doesn't include a framework that uses webpack, I'd recommend animate.css instead.

There are docs planned that will be released within the previously mentioned JS framework. 

A Tailwind plugin is also in the works. 
