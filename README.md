﻿# Thymeleaf And TailwindCSS

 Install and Set up Tailwind CSS
We will install Tailwind CLI from the NPM; before that, let's init a new Node.js project by running this command at the project root directory :

npm init -y
Install the node package:

npm i -D tailwindcss
Generate the Tailwind CSS configuration file with this command:

npx tailwindcss init
A file named "tailwind.config.js" will be generated; open it and replace the content with this one:

module.exports = {
  content: ["./src/main/resources/templates/**/*.{html,js}"],
  theme: {
    extend: {},
  },
  plugins: [],
}
We indicate to Tailwind CLI where to look for files that contain the Tailwind CSS classes.

At the root project directory, create a folder named "styles," then add a file named "input.css," and finally add the code below inside:

@tailwind base;
@tailwind components;
@tailwind utilities;

Generate the CSS from Tailwind classes
We need to generate the required CSS using the CLI; the command requires two options:

The input: The CSS entry file to use; this file usually contains the Tailwind CSS base CSS, the global CSS of the application, and the CSS of the external packages used in the project.
The output: The path where to generate the CSS output.
Here is the command to run:

npx tailwindcss -i styles/input.css -o ./src/main/resources/static/css/main.css
The output path is the static folder, and the name is "main.css."

After running the command, you will see the file at the expected location. Add the code below in the head's tag of the home.html.

<link rel="stylesheet" th:href="@{/css/main.css}" />
Thymeleaf will resolve the path, so the CSS is served as expected.

Rerun the application and watch the result

Watching Tailwind CSS classes
Every time you add or remove a class in your HMTL file, you need to rebuild your CSS file; this is not a good developer experience. Fortunately, the Tailwind CSS CLI provides an option to watch files and rebuild the CSS on change. Just add the option "--watch" to the previous command.

npx tailwindcss -i styles/input.css -o ./src/main/resources/static/css/main.css --watch
