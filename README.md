# @nnexCSS 

```bash
npm i annexcss
```
```bash
import 'annexcss'
```

# What is AnnexCSS?

AnnexCSS is a lightweight CSS animation library made for use with Next.js in a TBA front-end framework. It can be used independently with any web framework or project.

Modern browsers can properly handle unused styling so there are no special bells or whistles. Most modern CSS libraries overlook this and add unnecessary bloat to their project. When used in a framework like Next or Gatsby you get all the benefits of minification as well.

If you are using this library without a framework that provides automatic minification adding postcss with cssnano to your project can help you easily minify. It is simply one big CSS file and easy to target.

So how does it work? AnnexCSS first creates variables in :root to reuse as basic properties. 


```CSS

:root {

    --animate-repeat: 1;
    --animate-duration: 1s;
    --animate-delay: 1s;

}

```

It then wraps all elements (*) with some required core properties for individual classes to function properly. All classes use this wrapper when applied.

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
 
In regards to browser compatibility AnnexCSS focuses entirely on webkit. This covers the vast majority of users. Postcss with autoprefixer can assist you if you need to expand cross-compatibility. Classes typically look like this:

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

You can easily add these animations to your JSX or markup just like any regular CSS class. All AnnexCSS classes are prefixed with an @ symbol. This library was originally compiled using a custom animate.css build so you may see similar classes to the popular library. 

The major difference - AnnexCSS wraps all elements instead of individually applying base animation properties as needed. Seeing as hundreds of animations aren't typically needed in any given website and modern browsers override/remove unneeded styling performance hits using this method are entirely negligible.

|                   |                    |                     |                      |
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



```HTML

<div className="@fadeIn container"> I love potato </div>

```
You can extend functionality by adding utility classes like so:

```HTML

<div class="@fadeIn flex">
  <div class="@fadeIn @delay-1s flex-none ...">
    01 Potato
  </div>
  <div class="@fadeIn @delay-2s flex-1 w-64 ...">
    02 Potato
  </div>
  <div class="@fadeIn @delay-3s flex-1 w-32 ...">
    03 Potato
  </div>
</div>

```

And that's all there is to it!

There are docs planned that will be released alongside the previously mentioned JS framework. 

AnnexCSS is made to compliment TailwindCSS classes and expand on animations, but using Tailwind is not a requirement. It works just fine with regular CSS. 

A Tailwind plugin is planned in the near future and will be provided as an installation option. In the event you are using an extremely large amount of animations using the plugin would be the recommended option for maximizing optimization.

Contributions are welcome but the focus is optimization. I'm only looking to extend classes if they relate to classic commonly used processing techniques. There will be a dicussion for this in the frameworks repo.