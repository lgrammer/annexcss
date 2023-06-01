# @nnexCSS 

```
npm install annexcss
```

AnnexCSS is a lightweight CSS animation library made for use with Next.js in a TBA front-end framework. This library should also work well with any project or framework that minifies your CSS files.

AnnexCSS is made to compliment TailwindCSS classes and expand on animations, but using Tailwind is not a requirement. It works just fine with regular CSS. 

It is simply pure CSS and the build size is negligible when minified. There is practically no overhead.

If using in a project without automatic minification, postcss with cssnano can help you easily minify.

There will be a Tailwind plugin for this library in the near future. 

I'm hoping a tailwind plugin will create even smaller overhead. AnnexCSS will be benchmarked against its plugin (annexcss-tailwind) in a Tailwind/NextJS environment.

So how does it work? AnnexCSS first creates variables in :root to reuse as basic properties. 
```

:root {

    --animate-repeat: 1;
    --animate-duration: 1s;
    --animate-delay: 1s;

}

```

It then wraps all elements (*) with some required core properties for individual classes to function properly. All classes use this wrapper when applied.

```
* {
  
    animation-duration: 1s;
    animation-duration: var(--animate-duration);
    animation-fill-mode: both;
    -webkit-animation-fill-mode: both;
    -webkit-animation-duration: var(--animate-duration);
    -webkit-animation-duration: 1s;

}
```
Classes typically look like this:

```
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

You can easily add these animations to your JSX or MDX just like a regular CSS class. All AnnexCSS animation classes are prefixed with an @ symbol.


``` 

<div className="@fadeIn container"> I love potato </div>

```
You can extend functionality by adding utility classes like so:

```

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

There are docs planned. They will be released alongside a TBA Next.js front-end framework. 

Contributions are welcome. This project will accept any contribution that adds a new class. No repeats or modifications pls.