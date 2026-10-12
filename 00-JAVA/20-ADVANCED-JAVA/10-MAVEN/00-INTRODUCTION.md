# Introduction To Maven

### What is Maven?
- Maven is a **Build Tool** which is used to compile Java source code, package compiled classes into JAR files, and perform other build-related tasks. 
- Maven is a **Dependency Management Tool** which is used to manage external libraries (JAR files) required by a project.
- Maven is also a **Project Management Tool** which provides a standard project structure and manages project information and build configurations.
### Create a Maven Project in Eclipse
1. Navigate to **File → New → Maven Project**.
2. Choose a suitable project location and click **Next**.
3. Inside the **Catalog** section, choose `Internal`.
4. Select the following archetype:
    `org.apache.maven.archetypes : maven-archetype-quickstart : 1.1`
5. Click **Next**.
### Configure the Maven Project
Fill in the following fields:
- **GroupId** → Identifies the project's organizational namespace. It can represent a company, organization, or functional area (e.g., `com.bank.payment`).
- **ArtifactId** → Identifies the specific project or artifact (e.g., `payment-service`).
- **Version** → Identifies the particular version of the project.
### Example 1: Different GroupIds for Different Functional Areas

|Project|`groupId`|`artifactId`|
|---|---|---|
|Payment Service|`com.bank.payment`|`payment-service`|
|Authentication Service|`com.bank.security`|`authentication-service`|
|Notification Service|`com.bank.notification`|`notification-service`|
|Transaction Service|`com.bank.fintech`|`transaction-service`|

### Example 2: Same GroupId for All Projects

|Project|`groupId`|`artifactId`|
|---|---|---|
|Payment Service|`com.bank`|`payment-service`|
|Authentication Service|`com.bank`|`authentication-service`|
|Notification Service|`com.bank`|`notification-service`|
**Note:** Both approaches are valid. The company can choose a naming convention according to its project organization.
### Understanding Java Packages
A **package** is used to organize related Java classes and interfaces.

Package names often follow the same naming convention as the `groupId`, but a package is not necessarily a combination of `groupId` and `artifactId`.

For example, a project might contain the following packages:
- `com.bank.payment.model`
- `com.bank.payment.service`
- `com.bank.payment.repository`

These packages organize classes according to their responsibilities.
For example:
- `model` → Contains model classes.
- `service` → Contains business logic.
- `repository` → Handles data access.

### Understanding Version Numbers
A common versioning convention is **Semantic Versioning (MAJOR.MINOR.PATCH)**.

|Version|Typical meaning|
|---|---|
|`0.0.1`|An early development release|
|`0.1.0`|An early release with some functionality|
|`0.9.0`|Development nearing the first stable release|
|`1.0.0`|First stable release|
|`1.0.1`|Bug fixes to version `1.0.0`|
|`1.1.0`|Backward-compatible new functionality|
|`2.0.0`|Changes that may break backward compatibility|

**Note:** These meanings follow common versioning conventions; Maven itself does not enforce them.
For a project under initial development, you can use `0.0.1`. Once the project is ready for its first stable release, you can use `1.0.0`.
## Finish Project Creation
1. Fill in the `GroupId`, `ArtifactId`, and `Version` fields.
2. Click **Finish**.
3. If the console asks for confirmation, enter `Y` or `y` and press **Enter**.

Maven will generate the project structure based on the selected archetype.