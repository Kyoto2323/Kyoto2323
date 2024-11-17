Activity 25: SOLID PRINCIPLES in Angular
HASHNODE LINK: https://markromano69.hashnode.dev/activity-25-solid-principles-in-angular#heading-5-dependency-inversion-principle-dip


1. Single Responsibility Principle (SRP):
Definition: A class should have only one reason to change, meaning it should only have one job or responsibility.

In Angular: In Angular, SRP can be applied to components, services, and classes. Each Angular class should be responsible for only one task, reducing the chances of side effects when changes are made.

Example: If you have a service that handles both data fetching and user authentication, it's better to split these responsibilities into separate services. This makes your code more testable and easier to maintain.

Use Case: A real-world example of SRP in Angular is splitting the logic of handling form validation and API requests into different services to ensure each service has a single responsibility.



// Incorrect: Combining two responsibilities in one service
@Injectable({
  providedIn: 'root'
})
export class UserService {
  constructor(private http: HttpClient) {}

  // Responsible for fetching user data and authentication
  getUserData() { ... }
  login() { ... }
}
// Correct: Separate responsibilities into different services
@Injectable({
  providedIn: 'root'
})
export class UserDataService {
  constructor(private http: HttpClient) {}

  getUserData() { ... }
}

@Injectable({
  providedIn: 'root'
})
export class AuthService {
  constructor(private http: HttpClient) {}

  login() { ... }
}

2. Open/Closed Principle (OCP):
Definition: Software entities (classes, modules, functions) should be open for extension but closed for modification.

In Angular: Angular services, directives, and components can be extended without altering their existing code by using inheritance, abstract classes, or interfaces.

Example: You can create a base service that provides common functionality and extend it to create more specific services.

Use Case: A common application of OCP in Angular is creating base classes for components or services that handle common logic, while specific components extend them to add more specific behavior.



// Base Service (Open for Extension)
export class BaseService {
  getData() { ... }
}

// Extended Service (Closed for Modification)
@Injectable({
  providedIn: 'root'
})
export class ExtendedService extends BaseService {
  fetchData() { ... }
}


3. Liskov Substitution Principle (LSP):
Definition: Objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program.

In Angular: In Angular, ensure that your services, components, and directives are replaceable. This can be done through interfaces and inheritance, ensuring that subclasses or replacements do not break functionality.

Example: If you have a base class for a service, subclasses should follow the same method signature so that they can be replaced without causing issues.

Use Case: In an e-commerce application, different types of payment methods (e.g., credit card, PayPal) can implement a common payment interface to ensure they can be swapped easily without affecting the flow of transactions.



// Correct Implementation of LSP
export interface UserService {
  getUserData(): Observable<any>;
}

@Injectable({
  providedIn: 'root'
})
export class BasicUserService implements UserService {
  getUserData() { return ... }
}

@Injectable({
  providedIn: 'root'
})
export class PremiumUserService implements UserService {
  getUserData() { return ... }
}

// Both BasicUserService and PremiumUserService can be used interchangeably

4. Interface Segregation Principle (ISP):
Definition: No client should be forced to depend on methods it does not use.

In Angular: This principle is useful when defining services and interfaces. Instead of creating large interfaces with unnecessary methods, create smaller, focused interfaces that only include the methods relevant to a specific client.

Example: Instead of a large, monolithic service that implements unnecessary methods, split the service into more granular interfaces.

Use Case: In Angular, separating API calls into distinct services like AuthService, UserService, and OrderService ensures that each service has only the methods needed by the components that use them.



interface UserService {
  login();
  register();
  getUserData();
  getOrders();
}


interface AuthService {
  login();
  register();
}

interface UserDataService {
  getUserData();
  getOrders();
}


5. Dependency Inversion Principle (DIP):
Definition: High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions.

In Angular: Angular's dependency injection (DI) system naturally follows this principle. High-level components depend on abstractions (interfaces or services) rather than concrete implementations.

Example: Instead of directly instantiating a service inside a component, inject the service through the constructor.



(
{
  selector: 'app-user',
  templateUrl: './user.component.html'
})
export class UserComponent {
  constructor(private userService: UserService) {}
}



HASHNODE LINK: https://markromano69.hashnode.dev/activity-25-solid-principles-in-angular#heading-5-dependency-inversion-principle-dip









