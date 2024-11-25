## ![Angular](https://img.shields.io/badge/angular-DD0032?style=for-the-badge&logo=angular&logoColor=white)

Angular is a platform and framework for building single-page client applications using HTML and TypeScript. Angular is written in TypeScript. It implements core and optional functionality as a set of TypeScript libraries that you import into your applications.

### :star: Give a Star!

Support this research by **giving it a star**. Thanks!

| #Sr No | Name                         | Tags                   | Description |
| ------ | ---------------------------- | ---------------------- | ----------- |
| 1      | 📂 Angular Folders usage     | `Angular`, `Front end` |             |
| 2      | 🚃 Angular SOLID Principles  | `Angular`, `Front end` |             |
| 3      | 💉 Mastering DI              | `Angular`, `Front end` |             |
| 4      | 📊 Angular Signals           | `Angular`, `Front end` |             |
| 5      | 🏗️ PWA (Progressive Web App) | `Angular`, `Front end` |             |

<details>
    <summary><b>📂 Angular Folders usage</b></summary>

## Introduction

In an Angular project, the folder structure is designed to help organize the application into logical segments. Here’s an overview of common folders and files in an Angular project and their usages:

### 1. **`src/`** (Source folder)

This is where most of the Angular app’s development work is done.

- **`app/`**
  This is the core folder of your Angular application. It contains the components, services, modules, and other application logic. You can structure it into subfolders based on features for better scalability.
  - **`app.component.ts`**: Defines the root component of the application.
  - **`app.component.html`**: HTML template associated with the root component.
  - **`app.component.css`**: Styles specific to the root component.
  - **`app.module.ts`**: The root module of your application, defining the components and services your app uses.
- **`assets/`**
  A folder for storing **static files** such as images, fonts, and icons that are needed in your application. They are accessible via the `/assets` path.
- **`environments/`**
  This folder contains environment-specific configuration files.
  - **`environment.ts`**: Used during development.
  - **`environment.prod.ts`**: Used during production builds, often with different API endpoints or feature toggles.

### 2. **Configuration Files**

- **`angular.json`**
  The configuration file for the Angular CLI. It specifies settings like **build options, file paths, and scripts.** This file is crucial for customizing the build process and configuring the behavior of the Angular CLI.
- **`package.json`**
  This file **lists the project’s dependencies, scripts, and metadata like the project name and version.** It is critical for managing Node.js dependencies and defining the development commands (like `ng serve`, `ng build`).
- **`tsconfig.json`**
  The TypeScript configuration file. It specifies compiler options, such as module formats, target ECMAScript versions, and paths to be used by the TypeScript compiler.
- **`polyfills.ts`**
  This file is used to include polyfills required by your app for backward compatibility with older browsers. This is especially important when working with newer JavaScript features.
- **`styles.scss` or `styles.css`**
  Global styles for the Angular application. These styles are applied across all components unless overridden by component-specific styles.
- **`main.ts`**
  The entry point of the Angular application. This file bootstraps the root module (`AppModule`) to launch the app.
- **`index.html`**
  The main HTML file of the application. It contains the root component (`<app-root></app-root>`) and references stylesheets and scripts. This file is rendered when you serve the application.
- **`favicon.ico`**
  The default Angular favicon, which appears in the browser tab. You can replace this with your custom icon.

### 3. **Testing Files**

- **`karma.conf.js`**
  Configuration for Karma, the test runner for Angular applications. It defines the settings for running unit tests.
- **`protractor.conf.js`**
  Configuration for Protractor, the end-to-end testing framework for Angular. It is used for writing and executing integration tests.

### 4. **`node_modules/`**

This folder contains all of the project dependencies installed via npm. You typically don’t modify this folder directly, but it holds packages and libraries your application depends on.

### 5. **`dist/`** (Distribution folder)

This folder is generated when you build your Angular application. It contains the optimized files ready for deployment to production.

### 6. **`e2e/`** (End-to-End testing folder)

This folder is where end-to-end test files are stored. Protractor is typically used for these tests.

</details>

<details>
    <summary><b>🚃 Angular SOLID Principles</b></summary>
</details>

### Authors

> See the list of [contributors](https://github.com/SrikrushnaP) who participated in this project.

### License

This project is licensed under the MIT License
