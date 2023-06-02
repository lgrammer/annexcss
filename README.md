# @nnexCSS 

```bash

npm i annexcss


```

At the top of your entry file:

```bash

import 'annexcss'

```

# What is AnnexCSS?

AnnexCSS is a lightweight CSS animation library made for use with Next.js in a TBA front-end framework. It can be used independently with any web framework or project.

When coupled with frameworks like Next or Gatsby the browser can properly handle unused styling, so there are no special bells or whistles. Most modern CSS libraries overlook this and add unnecessary bloat to their project.

The goal is to keep the unpacked size as low as possible. That being said postcss-purgecss will be configured in the accompanying JS framework to minmax optimization for both build times and performance.

It is simply pure CSS and the current build size is already negligible when minified. There is practically no overhead in regards to build time or performance.

If using in a project without automatic minification, postcss with cssnano can help you easily minify.

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
 
In regards to browser compatibility AnnexCSS puts focus on webkit. Autoprefixer can assist you if you need to expand cross-compatibility. Classes typically look like this:

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

You can easily add these animations to your JSX or markup just like a regular CSS class. All AnnexCSS classes are prefixed with an @ symbol. This library was originally compiled using a custom animate.css build so you may see similar classes to the popular library. 


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

There are docs planned that will be released alongside a TBA Next.js front-end framework. 

AnnexCSS is made to compliment TailwindCSS classes and expand on animations, but using Tailwind is not a requirement. It works just fine with regular CSS. 

A Tailwind plugin is planned in the near future.

Contributions are welcome but the focus is optimization. I'm only looking to extend classes if they relate to classic commonly used processing techniques. There will be a dicussion for this in the frameworks repo.