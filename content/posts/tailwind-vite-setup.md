---
title: How I set up my Vite React Tailwind Storybook projects
date: 2023-04-20T19:00:00-07:00
tags: ['Vite', 'React', 'Tailwind']
---

I've been working on a lot of projects lately that use Tailwind for styling. On top of Tailwind, I've started to implement and familiarize myself with Storybook, which should help jumpstart the front-end dev process. Here's how I get my projects / learning / Tailwind Storybook exercises set up: 


**Tailwind Setup (Vite + React)**
<br>
1. Create a Vite + React project and add Tailwind
```
npm create vite@latest [my-project] -- --template react
cd [my-project]
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

2. Update the content key within tailwind.config.js
```
// your JavaScript code here

/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{html,js}"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

3. Add the Tailwind directives to src/index.css and remove the default CSS
```
@tailwind base;
@tailwind components;
@tailwind utilities;
```


**Storybook Setup**
1. Add storybook
```
npx sb init
```

2. Import the index.css into the .storybook/preview.js
```
import "../src/index.css";

/** @type { import('@storybook/react').Preview } */
const preview = {
  parameters: {
    actions: { argTypesRegex: "^on[A-Z].*" },
    controls: {
      matchers: {
        color: /(background | color)$/i,
        date: /Date$/,
      },
    },
  },
};
```

3. Use Tailwind in components!

In two terminals, run:
```
npm run dev
```
```
npm run storybook
```
After following those step, you should have a Vite + React + Tailwind + Storybook project set up.

<hr>

**Links**
- [Storybook + Tailwind Documentation](https://storybook.js.org/recipes/tailwindcss)
- [Tailwind Documentation](https://tailwindcss.com/docs/installation)