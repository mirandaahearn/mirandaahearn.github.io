# Miranda Ahearn | Computer Science Capstone ePortfolio

## Professional Self-Assessment

The Computer Science program at Southern New Hampshire University has been a three year journey that has built technical depth across software engineering, algorithms and data structures, database design, secure coding, and software testing. The goal coming out of this program is to transition into a product management role at a SaaS company, where the combination of technical fluency developed throughout this coursework and cross-functional communication experience gained working as a technical account manager creates a profile that is well suited to bridging engineering and business in a fast-moving product environment.

The ePortfolio presented here demonstrates that growth through three enhanced artifacts, each targeting a distinct computer science category and a distinct set of course outcomes. Rather than describing skills in abstract terms, each enhancement shows the actual work, the reasoning behind the decisions made, and the professional standards those decisions align with. For a product manager, technical transparency is what paves the way for credible conversations with engineering teams, the ability to write acceptance criteria that reflects how software functions, and the ability to recognize when technical shortcuts introduce product risk before they reach users.

The CS 410 Reverse Engineering Project Two addresses software engineering and design. The original artifact identified five security vulnerabilities through reverse engineering a compiled C++ binary, including a hardcoded plaintext password, unlimited login attempts, unvalidated user input, global variable exposure, and sensitive data disclosure in the display function. The enhancement refactored the entire program to address each vulnerability, replacing the plaintext credential with a hashed verification process, moving global variables into local scope, consolidating all input validation into a single reusable function, and restructuring the program into clearly defined single-responsibility functions. This work demonstrates outcome three through the trade-off analysis involved in introducing hashing complexity in exchange for security gain, outcome four through the application of professional C++ development standards aligned with OWASP guidelines, and outcome five as the foundation of the entire enhancement since every change directly addressed a specific adversarial exploit.

The CS 320 Contact Service addresses algorithms and data structures. The original artifact managed a collection of Contact objects using a HashMap with JUnit 5 unit tests covering basic happy path and failure scenarios. The enhancement introduced a TreeMap alongside the existing HashMap to support alphabetical sorted retrieval by last name without sacrificing the O(1) average lookup performance of the primary structure, and substantially expanded the test suite using JUnit 5 parameterized testing and exception message validation to achieve professional coverage standards. This work demonstrates outcome one through the transparency and readability of the expanded test documentation for both technical and non-technical stakeholders, outcome three through the algorithmic trade-off between memory overhead and sorted retrieval capability, outcome four through the use of industry-standard Java Collections Framework and JUnit 5 tooling, and outcome five through boundary condition and null input testing that anticipates how data can be misused.

The CS 465 Travlr Getaways application addresses databases. The original artifact supported full CRUD operations on a single trips collection in MongoDB with no relational modeling and no analytical query capability. The enhancement introduced a new bookings collection with an ObjectId reference to the trips collection, added POST and GET endpoints with JWT authentication and input validation, and implemented three MongoDB aggregation pipelines exposed through a new analytics endpoint that returns total bookings per trip, average price per resort, and trip distribution by departure month. This work demonstrates outcome two through the analytics endpoint which transforms raw database results into structured output consumable by product and business stakeholders, outcome three through the data modeling trade-off between embedding and referencing, outcome four through MongoDB aggregation pipelines which are the industry-standard tool for analytical queries in document-oriented databases, and outcome five through the input validation and JWT authentication protecting all write endpoints.

Across all three enhancements, the agile and iterative approach studied throughout the program and applied in practice as a technical account manager is reflected in how each one builds on existing work without breaking what already functions. Each artifact was reviewed for what it could not do rather than just what was wrong with it, and each enhancement was scoped to address a real limitation in a professionally grounded way. The code review video walks through all three original artifacts before enhancement, the narratives document the technical decisions and their alignment to industry standards, and this self-assessment connects the full arc of the program to a career path where technical depth and cross-functional communication are not separate skills but the same skill applied at different levels of abstraction.

---

## Code Review

[Click here to watch the code review video](https://youtu.be/do1n_k_UBg4)

---

## Enhancement One: Software Engineering and Design

**Artifact:** CS 410 Reverse Engineering Project Two (C++)

**Original Code:** [View on GitHub](https://github.com/mirandaahearn/cs499-artifacts/tree/main/cs410)

**Enhanced Code:** [View on GitHub](https://github.com/mirandaahearn/cs499-artifacts/tree/main/cs410)

### Narrative

The artifact chosen for enhancement one, Software Engineering and Design, is the CS 410 Reverse Engineering Project Two. The artifact, both original and enhanced, is a C++ console application that simulates a basic authentication and customer menu system. The original assignment involved analyzing a compiled binary, identifying security vulnerabilities through reverse engineering, and producing an annotated security report with a refactored version of the source code. The artifact was created in a previous term of the Computer Science program at Southern New Hampshire University. The piece of the artifact chosen for the ePortfolio was selected to highlight the ability to identify real security vulnerabilities in existing code and apply professional software engineering practices to address them, demonstrating not just that the problems exist but that the skills are in place to fix them in a meaningful and technically grounded way.

This artifact was selected for the ePortfolio because it demonstrates the ability to analyze existing code for security weaknesses, apply software engineering principles to refactor a flawed implementation, and produce a more secure and maintainable result. The CS 410 project provides a concrete foundation for enhancement because the original submission already identified the vulnerabilities through the reverse engineering process but left several of them unresolved. The enhancement builds on that foundation in a meaningful way as it aligns with industry best practices and creates more secure code that in a real world scenario would ensure stakeholders are protected.

The planned course outcomes for this enhancement were outcomes three, four, and five, which were met through the enhancements of this artifact.

**Outcome three:** designing and evaluating computing solutions while managing trade-offs. This outcome is demonstrated through the decision to introduce password hashing at the cost of added complexity. The trade-off between a simple plaintext comparison and a hash-based verification process was evaluated, and the security gain was determined to justify the additional implementation complexity. In the original code, the password was stored as a hardcoded global string and compared directly against user input using a basic equality operator, a design that is both functionally simple and foundationally insecure. The enhanced version replaces this with a hashPassword function that processes the input before any comparison is made, meaning the raw credential is never directly evaluated at any point in the program's execution. The decision to use a dual-scope approach for the customerChoice variable, local in main and passed as a parameter to the functions that need it, also reflects the design evaluation implemented. Moving the variable into local scope makes the data flow predictable and easy to identify, which is a principle of maintainable software design.

**Outcome four:** using well-founded and innovative techniques to implement industry-specific solutions. This outcome is demonstrated through the application of hash-based credential storage, the consolidation of input validation into a single reusable getValidatedInput function, and the structural reorganization of the program into clearly defined single-responsibility functions. The hash-based authentication approach aligns with OWASP secure coding guidelines for credential storage, and the single-responsibility design reflects the software engineering principle that each function should do exactly one thing and do it well.

**Outcome five:** developing a security mindset that anticipates adversarial exploits and mitigates design flaws. Each change made to the program directly addresses a specific adversarial exploit that was identified during the original reverse engineering process. The hardcoded plaintext credential was the most critical vulnerability, as it exposed the password to anyone with access to the source file. The global variable scope of customerChoice was identified as a shared state risk, the ChangeCustomerChoice function accepted unvalidated input directly from cin, and the DisplayInfo function was printing the username to the console. All of these were addressed in the enhancement.

**Reflection:** While reflecting on the enhancements made, the most significant challenge was implementing the password hashing component. Working through how hashing functions in practice took time, specifically understanding that the same input must always produce the same output and that the stored value and the input value must both go through the same hashing function before any comparison is made. Once the mechanics were understood and the code ran correctly, it was clear the concept had been successfully demonstrated.

---

## Enhancement Two: Algorithms and Data Structures

**Artifact:** CS 320 Contact Service (Java)

**Original Code:** [View on GitHub](https://github.com/mirandaahearn/cs499-artifacts/tree/main/cs320)

**Enhanced Code:** [View on GitHub](https://github.com/mirandaahearn/cs499-artifacts/tree/main/cs320)

### Narrative

The artifact chosen for enhancement two, Algorithms and Data Structures, is the CS 320 Contact Service project, completed during CS 320: Software Testing, Automation, and Quality Assurance. The artifact consists of three Java files. Contact.java defines the Contact object with field-level validation enforced in the constructor and setters. ContactService.java manages a collection of Contact objects using a HashMap data structure and supports add, delete, update, and retrieve operations. The test files contain JUnit 5 unit tests for both the Contact class and the ContactService class. The original artifact was created in a previous term of the Computer Science program at Southern New Hampshire University.

The piece of the artifact chosen for the ePortfolio was selected to highlight the ability to evaluate an existing data structure design, identify its limitations, and apply a more sophisticated algorithmic approach to address a real gap in the original implementation. The CS 320 Contact Service provides a strong foundation because the original HashMap design is efficient for direct ID-based lookups but had no mechanism for ordered retrieval. The enhancement introduces a dual data structure design and expands the test suite to reflect professional coverage standards.

The planned course outcomes for this enhancement were outcomes one, three, four, and five, which were met through the enhancements of this artifact.

**Outcome one:** employing strategies for building collaborative environments that enable diverse audiences to support organizational decision making. This outcome is demonstrated through the expanded test suite, which produces testing documentation that is readable and meaningful to both technical and non-technical stakeholders. A well-structured and thoroughly documented test suite is not just an engineering artifact. In a product environment it is a communication tool that helps product managers, QA leads, and business stakeholders understand what the software is expected to do, where the boundaries are, and what happens when those boundaries are crossed.

**Outcome three:** designing and evaluating computing solutions while managing trade-offs. This outcome is demonstrated through the decision to introduce a TreeMap alongside the existing HashMap rather than replacing it. Adding a second data structure increases the memory footprint of the service, but it provides sorted retrieval at O(log n) cost without degrading the O(1) average performance of the primary lookup path.

**Outcome four:** using well-founded and innovative techniques to implement industry-specific solutions. This outcome is demonstrated through the use of the Java Collections Framework TreeMap and JUnit 5 parameterized testing, both of which are industry-standard tools used in professional Java development environments.

**Outcome five:** developing a security mindset that anticipates adversarial exploits and mitigates design flaws. This outcome is addressed through the expansion of boundary condition and null input tests across all fields in the Contact class, anticipating how data can be misused and confirming that each case throws the correct exception with the correct message.

**Reflection:** One of the earliest challenges was deciding whether these were the right enhancements to choose in the first place. The original Contact Service worked correctly as submitted, which made it harder to identify where the value of enhancement actually lived. It took stepping back and thinking about what the data structure could not do before the TreeMap approach became clear. Once that decision was made, working through the TreeMap logic itself was the next challenge, specifically understanding that the key had to be constructed in a way that handled contacts sharing the same last name, and that the key had to be updated any time a last name changed or the sorted order would become stale.

---

## Enhancement Three: Databases

**Artifact:** CS 465 Travlr Getaways (MongoDB / Node.js)

**Original Code:** [View on GitHub](https://github.com/mirandaahearn/cs499-artifacts/tree/main/cs465)

**Enhanced Code:** [View on GitHub](https://github.com/mirandaahearn/cs499-artifacts/tree/main/cs465)

### Narrative

The artifact chosen for enhancement three, Databases, is the Travlr Getaways full stack web application, developed during CS 465: Full Stack Development. The artifact is a travel booking platform built on the MEAN stack with MongoDB as the database, Express and Node.js for the backend API, Angular for the Single-Page Application admin frontend, and Handlebars for the server-side rendered public website. The original artifact was created in a previous term of the Computer Science program at Southern New Hampshire University.

The piece of the artifact chosen for the ePortfolio was selected to highlight the ability to extend an existing MongoDB database layer beyond basic CRUD operations into relational modeling and analytical query design. The original Travlr application supported full create, read, update, and delete operations on a single trips collection but had no mechanism for storing booking data, no relationships between collections, and no analytical query capability.

The planned course outcomes for this enhancement were outcomes two, three, four, and five, which were met through the enhancements of this artifact.

**Outcome two:** designing and delivering professional-quality communications adapted to specific audiences. The /api/analytics endpoint demonstrates this outcome by transforming raw MongoDB aggregation results into structured JSON output that product teams and business stakeholders can consume without ever interacting with the database directly.

**Outcome three:** designing and evaluating computing solutions while managing trade-offs. This outcome is demonstrated through the decision to use ObjectId references rather than embedding trip data directly inside each booking document. The reference approach adds a lookup stage to queries but keeps the data model normalized, which is the correct trade-off for a collection where trip details may change after a booking is created.

**Outcome four:** using well-founded and innovative techniques to implement industry-specific solutions. This outcome is demonstrated through the use of MongoDB aggregation pipelines, which are the industry-standard approach for analytical queries in document-oriented databases, and the Mongoose populate method for handling cross-collection references in a Node.js application.

**Outcome five:** developing a security mindset that anticipates adversarial exploits and mitigates design flaws. This outcome is addressed through the input validation added to the POST /api/bookings endpoint, which checks that all required fields are present, that numGuests is a valid number, and that guestEmail matches a valid email format before any data reaches the database.

**Reflection:** The database layer proved to be the most challenging of the three artifact categories overall. The bookings model was the first major challenge. After creating booking.js and registering it in db.js, the routes were returning errors because the Booking model was not being recognized by the controllers. The routes themselves presented a second challenge as the updated index.js file was not being picked up correctly, which meant the endpoints were returning 404 responses even after the controller logic was written. The error handler in app.js added a third layer of difficulty as Express was trying to render an error view template that did not exist, which masked the actual error. Once all three of those issues were resolved in sequence, the endpoints returned correct responses. The process of working through each failure layer by layer reinforced how important it is to understand not just how to write database code but how the full application stack connects from model registration through the route handler to the error response.

---

*CS 499 Computer Science Capstone | Southern New Hampshire University | Miranda Ahearn*
