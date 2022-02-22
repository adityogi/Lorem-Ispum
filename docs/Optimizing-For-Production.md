---
"title": Production in TailWind CSS
sidebar_position: 2
"Description": A utility-first CSS framework packed with classes like flex, pt-4, text-center and rotate-90 that can be composed to build any design, directly in your markup.
---

# Production in TailWind CSS

Tailwind CSS is incredibly performance focused and aims to produce the smallest CSS file possible by only generating the CSS you are *actually using* in your project.

Combined with minification and network compression, this usually leads to CSS files that are less than 10kB, even for large projects. 

For example, Netflix uses Tailwind for **[Netflix Top 10](https://top10.netflix.com/)** and the entire website delivers only 6.5kB of CSS over the network.

With CSS files this small, you don’t have to worry about complex solutions like code-splitting your CSS for each page, and can instead just ship a single small CSS file that’s downloaded once and cached until you redeploy your site.

For the smallest possible production build, we recommend minifying your CSS with a tool like **[cssnano](https://cssnano.co/)**, and compressing your CSS with **[Brotli](https://en.wikipedia.org/wiki/Brotli)**.

If you’re using Tailwind CLI, you can minify your CSS by adding the **`--minify`** flag:

```
npx tailwindcss -o build.css --minify
```

Then in the Package.json file under scripts add the following code.

```json
"build": "vite build"
```

Then in TailWind.config.js file under the `module.exports = {` add your file sources under name purge.

```jsx
purge: {
	content: ["./index.html"],
	enabled: true,
}
```

or you could add it globally like 

```jsx
purge: {
	enabled: true,
	content: ["./components/**/*.{html,js,jsx}", "./index.html"],
}
```

Then run `**npm run build**` in the terminal and an minified version should have been built.

Learn More by visiting [TailWindCSS Documentation](https://tailwindcss.com/docs/) 

### **Great now you have Build TailWindCSS in your Web Project**