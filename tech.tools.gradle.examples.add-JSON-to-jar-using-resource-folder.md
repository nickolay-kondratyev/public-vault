---
id: n9hdwmjyaxja9gx5xnm53dx
title: add-JSON-to-jar-using-resource-folder
desc: ''
updated: 1690397839458
created: 1690397819961
---

<details>
<summary>Query</summary>

In Gradle Java package. 

Lets say I have the following Packages:
- A
- B

A depends on B.

B package has JSON file. That B will read and expose the data from JSON file as java objects to package A.

Now this JSON file needs to be accessible at runtime when package A is using package B.

What are common ways to make this work in gradle java. 
</details>

<details>
<summary>Solution</summary>

To make the JSON file from package B accessible at runtime when package A is using it, you need to include the JSON file in the produced JAR for package B and then use Java's classloader mechanism to read the file. 

Here's how you can achieve this:

1. **Include the JSON file in the JAR**:
   
   Ensure the JSON file is located in the `src/main/resources` directory of package B. Gradle's Java plugin treats files in this directory as resources and will include them in the resulting JAR when you build the project.

   Your package B directory structure might look something like:
   ```
   B/
   ├── src/
   │   ├── main/
   │   │   ├── java/
   │   │   └── resources/
   │   │       └── yourFile.json
   │   └── test/
   ├── build.gradle.kts
   └── settings.gradle.kts
   ```

2. **Read the JSON file in package B**:

   Use Java's `ClassLoader` to read the resource from the JAR. Here's a helper method in package B to read the JSON file:

   ```java
   import java.io.InputStream;
   import java.io.InputStreamReader;
   
   public class BResourceReader {
       
       public InputStreamReader readJSONResource() {
           ClassLoader classLoader = getClass().getClassLoader();
           InputStream inputStream = classLoader.getResourceAsStream("yourFile.json");
           if (inputStream == null) {
               throw new RuntimeException("Cannot find resource: yourFile.json");
           }
           return new InputStreamReader(inputStream);
       }
   }
   ```

3. **Access the JSON data in package A**:

   Once you've included package B as a dependency in package A's `build.gradle.kts`, you can simply instantiate the `BResourceReader` class and invoke its method to get the JSON data:

   ```java
   import packageB.BResourceReader;
   
   public class A {
       
       public static void main(String[] args) {
           BResourceReader reader = new BResourceReader();
           // Now use the reader to get the JSON data
           InputStreamReader jsonReader = reader.readJSONResource();
           // ... process the JSON data using your preferred library
       }
   }
   ```

4. **Add package B as a dependency for package A**:

   In package A's `build.gradle.kts` file:

   ```kotlin
   dependencies {
       implementation(project(":B"))
   }
   ```

**TLDR**: 
- Put the JSON file in `src/main/resources` of package B.
- Use Java's `ClassLoader` to access the JSON file in package B.
- Add package B as a dependency in package A's `build.gradle.kts` and access the JSON data by invoking the method from package B.
</details>

