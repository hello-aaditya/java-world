# Java JAR Files and their Dependencies
Consider a team of Java developers developing an E-Commerce application. The duty of developers is to write code, compile it and generate `.class` files.

Suppose:
- DEV1 is working on Order Service and has generated 1000 classes.
- DEV2 is working on Payment Service and Delivery Service. For Payment Service he has generated 500 classes and for Delivery Service he has generated 700 classes.
## The Problem
The main question is — how their services will interact with each other?

For example, once payment is approved, only then end-user is allowed to go for Order Service. Once the order is confirmed, then the user is allowed to interact with Delivery Service.
- Order Service needs the code of Payment Service.
- Similarly, Delivery Service needs the code of Order Service.
DEV1 and DEV2 are working on their individual laptops and the source code stays with them only, so how will their services interact with each other? should they have to share entire codebase to each other?

## Solution
DEV2 will compile the Payment Service code and generate one JAR file (`payment-1.2.jar`) and give it to DEV1.
> **JAR (Java Archive)** -> all the compiled classes (`.class` files) bundled together.

DEV1 will add this JAR file as a dependency to the Order Service project.

Once DEV1 completes his work, he will again create one JAR and give it to DEV2 for Delivery Service.
## Why is JAR needed?
Question →

If one developer can send 500–700 individual `.class` files to another developer, then why do we need a JAR file?

Answer →

- **Easy to share:** Instead of sharing hundreds of individual files, we can bundle them into one JAR file.
- **Easy to manage:** All the related compiled classes and resources can be kept together in one file.
- **Reduces the risk of missing files:** If we share individual files manually then there might be a possibility that some files will be missed. But if create one JAR then we just have to send one file.
- **Code reuse:** Other developers can use the classes and methods available in the JAR file without needing the original source code.
## How to create a JAR inside Eclipse
1. Right-click the project > **Export**.
2. Select **Java > JAR file** (or search “JAR file”) > **Next**.
3. On the first page, select the resources to export. Keep “Export generated class files and resources” ticked. Then set the JAR file location and name in the “JAR file” field (Browse helps), e.g. `payment-1.0.jar`.
4. Click **Next** to see the packaging options. We can leave these as default.
5. Click **Next** again to see the manifest page. For a library JAR like Payment Service, we can leave the default.
6. Click **Finish**.
## Important JAR Commands
Java provides the `jar` command to create, view, and extract JAR files.
### 1. **View the contents of a JAR file**
```
jar -tvf myJar-1.0.jar
```
- `-t` → Lists the contents of the JAR file.
- `-v` → Displays detailed information.
- `-f` → Specifies the JAR file name.
**Use:** To check which `.class` files and other resources are present inside a JAR file.
### 2. Extract the contents of a JAR file
```
jar -xvf myJar-1.0.jar
```
- `-x` → Extracts the contents.
- `-v` → Displays the files being extracted.
- `-f` → Specifies the JAR file name.
**Use:** To extract the files from a JAR into the current directory.
To extract the files into a specific directory:
```
jar -xvf myJar-1.0.jar -C extracted/
```
### 3. Create a JAR file
```
jar -cvf myJar-1.0.jar -C classes .
```
- `-c` → Creates a new JAR file.
- `-v` → Displays detailed information.
- `-f` → Specifies the output JAR file name.
- `-C` → Changes to the specified directory before adding files.
- `.` → Includes all files and directories from the `classes` directory.
**Use:** To bundle compiled classes and resources into a JAR file.
Here, `classes` is assumed to contain the compiled `.class` files.
### 4. Extract a specific file from a JAR
```
jar -xvf myJar-1.0.jar com/example/PaymentService.class
```
**Use:** To extract only the specified class file instead of extracting the entire JAR.
The path must match the file's actual location inside the JAR.
### 5. Run an executable JAR file
```
java -jar myApp.jar
```
**Use:** To execute a JAR file configured with a valid `Main-Class` entry in its manifest.
**Note:** Not every JAR file is executable. A library JAR may contain classes intended to be used by another application.
### 6. Display the Java version
```
java -version
```
**Use:** To check the installed Java runtime version.
To check the version of the JAR tool:
```
jar --version
```
### Quick Revision

|Command|Purpose|
|---|---|
|`jar -tvf myJar-1.0.jar`|View JAR contents|
|`jar -xvf myJar-1.0.jar`|Extract all contents|
|`jar -cvf myJar-1.0.jar -C classes .`|Create a JAR|
|`jar -xvf myJar-1.0.jar path/to/File.class`|Extract a specific file|
|`java -jar myApp.jar`|Run an executable JAR|
|`jar --version`|Check JAR tool version|

**Important:** The `jar` command comes with the JDK. We can execute these commands from CMD or a terminal, provided the JDK's `bin` directory is available through our `PATH` or we use the full path to the executable.