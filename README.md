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

Let's break down the SOLID principles with Angular-specific examples and real-world metaphors to help you understand their application.

## **Metaphor** Examples :

| Name                                      | **Metaphor** Example                                                                                                                                                                           |
| ----------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Single Responsibility Principle (SRP)** | Think of a **Remote control.** Each button on the remote is responsible for a single action.                                                                                                   |
| **Open/Closed Principle (OCP)**           | Think of a **Smartphone**. You can add apps without modifying the phone's operating system. The system is open for extension (adding apps) but closed for modification (changing the core OS). |
| **Liskov Substitution Principle (LSP)**   | Consider a vending machine that dispenses snacks and drinks.                                                                                                                                   |
| **Interface Segregation Principle (ISP)** | Imagine a **Restaurant menu.** If the menu had only one page listing everything . it would be overwhelming. Instead, menus are often segmented, allowing diners to focus on what they want.    |
| **Dependency Inversion Principle (DIP)**  | Imagine you're **building a modular home**. Instead of constructing everything on-site, you build different parts (like the kitchen, living room, and bathroom) separately in a factory.       |

![Solid.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/20d02b6a-9399-4963-b3a0-5eae9f8cd709/0ff328c5-534c-4d12-9aeb-693bbc46e1f0/Solid.jpg)

- **1. Single Responsibility Principle (SRP)**
  **Metaphor:**
  Think of a remote control. Each button on the remote is responsible for a single action, like changing the channel, adjusting the volume, or turning the TV on/off. If you combine these functions into one button, it would be confusing and error-prone.
  **Angular Example:**
  Imagine you have a component in Angular that handles both data fetching and UI rendering. This violates the SRP because the component is doing too much. Instead, separate the responsibilities:

  ```tsx
  // Data service responsible for fetching data
  @Injectable({
    providedIn: "root",
  })
  export class DataService {
    constructor(private http: HttpClient) {}

    getData() {
      return this.http.get("api/data");
    }
  }

  // Component responsible for UI rendering
  @Component({
    selector: "app-data-display",
    templateUrl: "./data-display.component.html",
  })
  export class DataDisplayComponent implements OnInit {
    data: any;

    constructor(private dataService: DataService) {}

    ngOnInit() {
      this.dataService.getData().subscribe((data) => {
        this.data = data;
      });
    }
  }
  ```

  Here, the `DataService` is responsible for fetching data, while the `DataDisplayComponent` is responsible for rendering the UI. Each class has a single responsibility.

- **2. Open/Closed Principle (OCP)**
  **Metaphor:**
  Think of a smartphone. You can add apps without modifying the phone's operating system. The system is open for extension (adding apps) but closed for modification (changing the core OS).
  **Angular Example:**
  Imagine you need to add a new feature to log errors in an existing service. Instead of modifying the service directly, you can extend its functionality using inheritance or composition.

  ```tsx
  // Existing service
  @Injectable({
    providedIn: "root",
  })
  export class AuthService {
    login() {
      // logic for user login
    }
  }

  // Extended service with additional functionality
  @Injectable({
    providedIn: "root",
  })
  export class AuthServiceWithLogging extends AuthService {
    login() {
      console.log("Logging in user...");
      super.login();
      // this.router(
    }
  }
  ```

  Here, `AuthServiceWithLogging` extends `AuthService` without modifying the original `AuthService`. The code is open for extension but closed for modification.

- **3. Liskov Substitution Principle (LSP)**
  **Metaphor:**
  Consider a vending machine that dispenses snacks and drinks. If you substitute a snack with another snack (e.g., chips with cookies), the machine should still work. However, if you replace a snack with a non-edible item, the machine might break.
  **Angular Example:**
  Assume you have a base class `Animal` and derived classes `Dog` and `Bird`. According to LSP, you should be able to substitute a `Dog` object with a `Bird` object without breaking the functionality.

  ```tsx
  class Animal {
    makeSound() {
      // generic sound
    }
  }

  class Dog extends Animal {
    makeSound() {
      console.log("Woof!");
    }
  }

  class Bird extends Animal {
    makeSound() {
      console.log("Chirp!");
    }
  }

  // A function that works with the base class
  function playWithAnimal(animal: Animal) {
    animal.makeSound();
  }

  // LSP ensures that this works for any subclass
  let myDog = new Dog();
  let myBird = new Bird();
  playWithAnimal(myDog); // Outputs 'Woof!'
  playWithAnimal(myBird); // Outputs 'Chirp!'
  ```

  Here, substituting `Dog` with `Bird` doesn’t break the `playWithAnimal` function, adhering to LSP.

- **4. Interface Segregation Principle (ISP)**
  **Metaphor:**
  Imagine a restaurant menu. If the menu had only one page listing everything—appetizers, main courses, desserts, and drinks—it would be overwhelming. Instead, menus are often segmented, allowing diners to focus on what they want.
  **Angular Example:**
  Suppose you have an interface that enforces methods for multiple actions, but not all classes implementing this interface need all actions.

  ```tsx
  // Bad example: Single interface with too many responsibilities
  interface Worker {
    code(): void;
    design(): void;
    test(): void;
  }

  // Good example: Segregating interfaces
  interface Coder {
    code(): void;
  }

  interface Designer {
    design(): void;
  }

  interface Tester {
    test(): void;
  }

  class Developer implements Coder {
    code() {
      console.log("Writing code");
    }
  }

  class GraphicDesigner implements Designer {
    design() {
      console.log("Designing UI");
    }
  }
  ```

  Here, `Coder`, `Designer`, and `Tester` interfaces segregate responsibilities, ensuring that classes only implement what they need.

- **5. Dependency Inversion Principle (DIP)**

  - **Metaphor: Building a Modular Home**
    **Scenario:**
    Imagine you're building a modular home. Instead of constructing everything on-site, you build different parts (like the kitchen, living room, and bathroom) separately in a factory. Each module (part of the house) can be designed independently and then assembled together on-site.
    The key idea here is that the construction workers don’t need to know the specifics of each module’s internal workings. They simply connect the modules using standard interfaces (like electrical connectors, water pipes, etc.).
    Now, if you decide to change the kitchen module to a different design, you don't need to tear down the entire house. You can just swap out the kitchen module because it uses the same standard connections.
    **In terms of software design:**
    - The **modules** represent the high-level policy or logic (e.g., business rules or UI components).
    - The **connectors** represent the abstractions or interfaces that these modules rely on.
    - The **specific module implementations** represent the low-level details or classes (e.g., database access, API calls).
      By depending on abstractions (the connectors), the system remains flexible, allowing you to swap out low-level modules without affecting the high-level logic.
  - **Angular Example: Email Notification System**
    **Scenario:**
    You are building an Angular application that needs to send notifications to users. Initially, the notifications are sent via email, but later, the requirement might change to support SMS, push notifications, or even a combination of all three.
    **Without Dependency Inversion Principle:**

    ```tsx
    @Injectable({
      providedIn: "root",
    })
    export class NotificationService {
      constructor(private http: HttpClient) {}

      sendNotification(message: string) {
        // Directly using HttpClient to send an email
        this.http.post("api/sendEmail", { message }).subscribe();
      }
    }

    @Component({
      selector: "app-notification",
      templateUrl: "./notification.component.html",
    })
    export class NotificationComponent {
      constructor(private notificationService: NotificationService) {}

      notifyUser() {
        this.notificationService.sendNotification("Hello, User!");
      }
    }
    ```

    In this example:

    - The `NotificationService` is tightly coupled with the email-sending implementation.
    - If you need to change the notification method (e.g., to SMS), you have to modify the `NotificationService` directly, which violates the Dependency Inversion Principle.
      **With Dependency Inversion Principle:**
      **Step 1: Define an Abstraction**

    ```tsx
    export interface NotificationSender {
      send(message: string): void;
    }
    ```

    This interface defines the method that any notification sender must implement.
    **Step 2: Implement Concrete Classes**

    ```tsx
    @Injectable({
      providedIn: "root",
    })
    export class EmailNotificationSender implements NotificationSender {
      constructor(private http: HttpClient) {}

      send(message: string): void {
        this.http.post("api/sendEmail", { message }).subscribe();
      }
    }

    @Injectable({
      providedIn: "root",
    })
    export class SMSNotificationSender implements NotificationSender {
      send(message: string): void {
        // Logic to send SMS
        console.log("Sending SMS:", message);
      }
    }

    @Injectable({
      providedIn: "root",
    })
    export class PushNotificationSender implements NotificationSender {
      send(message: string): void {
        // Logic to send push notification
        console.log("Sending Push Notification:", message);
      }
    }
    ```

    Each class implements the `NotificationSender` interface but handles notifications in different ways (email, SMS, push notification).
    **Step 3: Depend on Abstractions in High-Level Modules**

    ```tsx
    @Injectable({
      providedIn: "root",
    })
    export class NotificationService {
      constructor(private notificationSender: NotificationSender) {}

      sendNotification(message: string) {
        this.notificationSender.send(message);
      }
    }

    @Component({
      selector: "app-notification",
      templateUrl: "./notification.component.html",
    })
    export class NotificationComponent {
      constructor(private notificationService: NotificationService) {}

      notifyUser() {
        this.notificationService.sendNotification("Hello, User!");
      }
    }
    ```

    Here:

    - The `NotificationService` depends on the `NotificationSender` abstraction, not a specific implementation.
    - The concrete implementation is injected into the service, so if you want to switch from email to SMS, you only need to change the injection configuration, not the high-level code.
      **Step 4: Configure Dependency Injection**
      In your Angular module, you can configure which implementation to use:

    ```tsx
    @NgModule({
      providers: [
        { provide: NotificationSender, useClass: EmailNotificationSender },
        // or for SMS:
        // { provide: NotificationSender, useClass: SMSNotificationSender },
        // or for Push:
        // { provide: NotificationSender, useClass: PushNotificationSender },
      ],
      declarations: [NotificationComponent],
    })
    export class AppModule {}
    ```

    **Benefits of this Approach:**

    1. **Flexibility:** You can easily switch between different notification methods without modifying the core logic.
    2. **Testability:** You can mock the `NotificationSender` interface in unit tests to simulate different behaviors without relying on actual HTTP requests.
    3. **Scalability:** If you need to add a new notification type (e.g., in-app notifications), you simply implement the `NotificationSender` interface, and the rest of the system remains unchanged.
       By following the Dependency Inversion Principle, your Angular application becomes more modular, maintainable, and adaptable to changing requirements.

- **Other Images and Links**
  !https://javatechonline.com/wp-content/uploads/2023/04/SOLID_Design_Principles-1.jpg

</details>

### Authors

> See the list of [contributors](https://github.com/SrikrushnaP) who participated in this project.

### License

This project is licensed under the MIT License
