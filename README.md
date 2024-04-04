<details>
<summary>Tutorial Module 7</summary>

<details>
<summary>Reflection Publisher-1</summary>

1. In the Observer pattern diagram explained by the Head First Design Pattern book, Subscriber is defined as an interface. Explain based on your understanding of Observer design patterns, do we still need an interface (or **trait** in Rust) in this BambangShop case, or a single Model **struct** is enough?

    In the BambangShop scenario, employing an interface or trait for the Subscriber in the Observer pattern remains beneficial. Such an approach allows for abstraction and decoupling between the Subject and its observers, promoting flexibility, scalability, and easier testing. By defining a contract for subscribers, interfaces or traits ensure consistency and enforce necessary behaviors, enhancing maintainability and extensibility in the system design. Therefore, even in a simplified structure like BambangShop, utilizing an interface or trait for subscribers aids in achieving loosely coupled and adaptable code architecture.

2. **id** in **Program** and **url** in **Subscriber** is intended to be unique. Explain based on your understanding, is using **Vec** (list) sufficient or using **DashMap** (map/dictionary) like we currently use is necessary for this case?

    In a scenario where unique identifiers (**id** in **Program** and **url** in **Subscriber**) are essential, choosing between a **Vec** (list) and a **DashMap** (map/dictionary) depends on the requirements. While a **Vec** could suffice for merely maintaining a collection of elements, ensuring uniqueness would require inefficient iterations over the entire list. In contrast, **DashMap** offers efficient lookup operations based on keys and guarantees uniqueness within the data structure. Given the necessity for unique identifiers and the potential need for efficient lookup operations, employing a **DashMap** would be more suitable, providing both integrity and performance to the system.

3. When programming using Rust, we are enforced by rigorous compiler constraints to make a thread-safe program. In the case of List of Subscribers (**SUBSCRIBERS**) static variable, we used the **DashMap** external library for **thread-safe HashMap**. Explain based on your understanding of design patterns, do we still need DashMap or we can implement Singleton pattern instead?

    In the context of managing a list of subscribers in a thread-safe manner in Rust, using DashMap from an external library offers a straightforward solution, providing built-in concurrency support for simultaneous access and modification. While the Singleton pattern could be considered for managing a single instance of the subscriber list, implementing it in Rust introduces challenges due to the language's ownership and borrowing rules, necessitating additional synchronization mechanisms like Mutex or RwLock to ensure thread safety. Ultimately, DashMap's dedicated concurrency handling makes it a more practical choice for managing the subscriber list in a thread-safe manner, offering simplicity and efficiency without the need for manual synchronization efforts.

</details>

<details>
<summary>Reflection Publisher-2</summary>

1. In the Model-View Controller (MVC) compound pattern, there is no “Service” and “Repository”. Model in MVC covers both data storage and business logic. Explain based on your understanding of design principles, why we need to separate “Service” and “Repository” from a Model?

    Separating the concerns of "Service" and "Repository" from the Model in an application architecture aligns with design principles such as the Single Responsibility Principle (SRP) and Separation of Concerns. By isolating responsibilities into distinct components, each layer can focus on a specific task: the Model encapsulates domain entities and behaviors, the Service layer manages application-specific business logic, and the Repository layer handles data access and storage. This separation enhances maintainability, scalability, and testability by enabling each component to evolve independently and promoting modularity and reusability across the system. Furthermore, it facilitates flexibility and adaptability, allowing for changes in business logic or data storage mechanisms with minimal impact on other parts of the application. Overall, this architectural approach promotes a clear and organized structure, improving the overall quality and maintainability of the codebase.

2. What happens if we only use the Model? Explain your imagination on how the interactions between each model (Program, Subscriber, Notification) affect the code complexity for each model?

    Relying solely on the Model without separating concerns into distinct layers like Service and Repository would lead to increased code complexity and potential coupling between different parts of the application. Each model (Program, Subscriber, Notification) would need to handle not only domain entities and behaviors but also business logic, data access, and storage concerns, resulting in bloated and intertwined code. This approach could make it challenging to maintain and extend the models over time, as they would be responsible for too many responsibilities. Additionally, mixing concerns within the models could lead to a lack of clarity and hinder the ability to make changes or add new features in a modular and maintainable way. Overall, separating concerns into distinct layers promotes a clearer separation of responsibilities and enhances the maintainability, scalability, and flexibility of the codebase.

3. Have you explored more about Postman? Tell us how this tool helps you to test your current work. Maybe you want to also list which features in Postman you are interested in or feel like it’s helpful to help your Group Project or any of your future software engineering projects.

    Postman is a powerful tool for API testing, development, and collaboration that offers features to streamline testing processes and enhance productivity for developers. With its user-friendly interface, developers can easily send HTTP requests to APIs and inspect responses, facilitating efficient testing of endpoints and early detection of bugs. Postman's organization capabilities, including collections and environments, enable developers to manage and execute tests across different environments with configurable variables, improving consistency and reproducibility. Additionally, features like automated testing, collaboration tools, monitoring, and mock servers further enhance its utility for software engineering projects, fostering better communication, productivity, and reliability in both individual and group endeavors.

</details>

<details>
<summary>Reflection Publisher-3</summary>

1. Observer Pattern has two variations: Push model (publisher pushes data to subscribers) and Pull model (subscribers pull data from publisher). In this tutorial case, which variation of Observer Pattern that we use?

    I think we are using the Push model because in the `notify` function, the Publisher (self) iterates over a list of Subscribers obtained from the `SubscriberRepository`, and for each Subscriber, it sends a notification by invoking the `update` method on the Subscriber with the relevant payload. This direct delivery of notifications from the Publisher to the Subscribers aligns with the Push model of the Observer Pattern.

2. What are the advantages and disadvantages of using the other variation of Observer Pattern for this tutorial case? (example: if you answer Q1 with Push, then imagine if we used Pull)

    Implementing the Pull variation of the Observer Pattern in the given tutorial case would offer advantages such as reduced overhead and controlled data retrieval. Subscribers would only request updates from the Publisher when needed, leading to efficient resource management. However, this approach could introduce potential drawbacks, including latency in update delivery, increased complexity in implementation due to the need for polling logic, and potential issues with increased network traffic if Subscribers poll frequently. Ultimately, the suitability of the Pull model depends on the specific requirements of the application and considerations regarding resource usage and system performance.

3. Explain what will happen to the program if we decide to not use multi-threading in the notification process.

    If multi-threading is not utilized in the notification process, the program would encounter blocking behavior as notifications are sent to subscribers sequentially. This means that each notification process would occur one after the other, potentially leading to delays and decreased efficiency, especially if any notifications encounter long-running tasks or delays. Without multi-threading, the program's responsiveness and scalability could be adversely affected, particularly in scenarios involving a large number of subscribers or time-consuming notification tasks. Overall, the absence of multi-threading would result in synchronous and sequential notification processing, potentially impacting performance and responsiveness.

</details>

</details>