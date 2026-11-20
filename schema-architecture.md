### Architecture summary
This Spring Boot application uses both MVC and REST controllers. Thymeleaf templates are used for the Admin and Doctor dashboards, while REST APIs serve all other modules. The application interacts with two databases—MySQL (for patient, doctor, appointment, and admin data) and MongoDB (for prescriptions). All controllers route requests through a common service layer, which in turn delegates to the appropriate repositories. MySQL uses JPA entities while MongoDB uses document models.
### flow of data and control
1. User accesses AdminDashboard or Appointment pages.
2. The action is routed to the appropriate Thymeleaf or REST controller.
3. The controller calls the service layer...
4. MySQL repositories are used to manage structured data, which is stored in MySQL Database, and MongoDB repository is used to communicate with Manago DB, where unstrucuture data is stored.
5. Structured entities, such as users, roles, and appointments, are storedin MySQL, while MongoDB stores flexible and nested data structures such as prescriptions.
6. Retrived data from MySQL are bounded into JPA entities, while data retrived from MongoDB is loaded into document objects.
7. In MVC flows, models are passed from controller to Thymeleaf templates, while in REST flows, the same models are serialized into JSON and sent back to the client.
