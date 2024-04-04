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

</details>