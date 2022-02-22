---
"title": Installation of TailWind CSS
sidebar_position: 1
"Description": A utility-first CSS framework packed with classes like flex, pt-4, text-center and rotate-90 that can be composed to build any design, directly in your markup.
---
# Installation

## Create your HTML File

```html live
<!DOCTYPE html>
<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <meta http-equiv="X-UA-Compatible" content="IE=edge">
	    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	    <link href="/Assets/CSS/style.css" rel="stylesheet">
	    <title>Document</title>
	</head>
	<body>
	    <h1>Hello World</h1>
	</body>
</html>
```

## **Add the Tailwind directives to your CSS File**

Add the **`@tailwind`** directives or each of Tailwind’s layers to your main CSS file.

These are shown below:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

## Creating the Package.json file

```
npm init -y
```

Install **`tailwindcss`** and its peer dependencies via 

```
npm install -D tailwindcss@latest postcss@latest autoprefixer@latest vite@latest
```

This will create a Files named **`package.lock.json`**. A new directory named `**node_modules**` will also be created.

## Create Tailwind and PostCSS Configuration File

This should create your **`tailwind.config.js`** and **`postcss.config.js`** file.

```
npx tailwindcss init -p
```

Tailwind CSS works by scanning all of your HTML, JavaScript components, and any other template files for class names, then generating all of the corresponding CSS for those styles.

In order for Tailwind to generate all of the CSS you need, it needs to know about every single file in your project that contains any Tailwind class names.

Configure the paths to all of your content files in the **`content`** section of your configuration file:

Paths are configured as **[glob patterns](https://en.wikipedia.org/wiki/Glob_(programming))**, making it easy to match all of the content files in your project without a ton of configuration:

- Use  **`*`**to match anything except slashes and hidden files
- Use **`**`** to match zero or more directories
- Use comma separate values between **`{}`** to match against a list of options

Tailwind uses the **[fast-glob](https://github.com/mrmlnc/fast-glob)** library under-the-hood — check out their [documentation](https://tailwindcss.com/docs/) other supported pattern features.

Open the package.json file and under scripts in place of “test” type  `**“start”: “vite”,**`.

Then in the Terminal type `**npm start**` to start your development server.

OR

Open the package.json file and under scripts in place of “test” type  `**“dev”: “vite”,**`.

Then in the Terminal type `**npm run dev**` to start your development server.

## **Build Tailwind CCS**

### Way 1

```
npx tailwindcss -i ./Assets/CSS/style.css -o ./build/tailwind.css --watch
```

### Way 2

Now open your `package.json` file, and add a scripts section if you don’t have it:

```json
"scripts": {
  "build:css": "postcss ./Assets/CSS/style.css -o dist/tailwind.css"
}
```

Now from the command line run `**npm run build:css**` will build the final CSS file.

The resulting file is in `dist/tailwind.css` (you can change the location in the above command).

## File Location

If you have any files you need to scan that are at the root of your project (often an **`index.html`** file), list that file independently so your other patterns can be more specific:

```js
module.exports = {
  content: [
		'./components/**/*.{html,js}',
    './pages/**/*.{html,js}',
		'./index.html',
	],
	// ...
}
```

Some frameworks hide their main HTML entry point in a different place than the rest of your templates (often **`public/index.html`**), so if you are adding Tailwind classes to that file make sure it’s included in your configuration as well.

If you have any JavaScript files that manipulate your HTML to add classes, make sure you include those as well.

It’s also important that you don’t scan any CSS files — configure Tailwind to scan your *templates* where your class names are being used, never the CSS file that Tailwind is generating.

Learn More by visiting [TailWindCSS Documentation](https://tailwindcss.com/docs/)

### **Great now you have installed TailWindCSS in your Web Project**
