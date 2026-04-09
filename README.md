# Experiment 12: Running JUnit Tests with Maven

## Objective
To configure Maven, write JUnit test cases, and execute them using Maven.

## Prerequisites
- Java JDK 17 installed
- Maven installed and configured
- Basic knowledge of Java and command line

## Project Structure

junit-demo/
│── pom.xml
└── src/
    ├── main/
    │   └── java/
    │       └── com/bnmit/
    │           └── Calculator.java
    └── test/
        └── java/
            └── com/bnmit/
                └── CalculatorTest.java

---

## Step 1: Create Maven Project

Run the following command in terminal:

mvn archetype:generate

Provide the following inputs:
- groupId: com.bnmit
- artifactId: junit-demo
- version: 1.0-SNAPSHOT

---

## Step 2: Configure pom.xml

<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
         http://maven.apache.org/xsd/maven-4.0.0.xsd">

    <modelVersion>4.0.0</modelVersion>

    <groupId>com.bnmit</groupId>
    <artifactId>junit-demo</artifactId>
    <version>1.0-SNAPSHOT</version>

    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>

    <dependencies>

        <!-- JUnit 5 -->
        <dependency>
            <groupId>org.junit.jupiter</groupId>
            <artifactId>junit-jupiter</artifactId>
            <version>5.9.3</version>
            <scope>test</scope>
        </dependency>

    </dependencies>

    <build>
        <plugins>

            <!-- Compiler Plugin -->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.11.0</version>
                <configuration>
                    <source>17</source>
                    <target>17</target>
                </configuration>
            </plugin>

            <!-- Surefire Plugin (Runs JUnit Tests) -->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-plugin</artifactId>
                <version>3.0.0</version>
            </plugin>

        </plugins>
    </build>

</project>

---

## Step 3: Create Java Class

File: src/main/java/com/bnmit/Calculator.java

package com.bnmit;

public class Calculator {

    public int add(int a, int b) {
        return a + b;
    }

    public int divide(int a, int b) {
        return a / b;
    }
}

---

## Step 4: Create Test Class

File: src/test/java/com/bnmit/CalculatorTest.java

package com.bnmit;

import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

public class CalculatorTest {

    Calculator calc = new Calculator();

    @Test
    public void testAdd() {
        assertEquals(5, calc.add(2, 3));
    }

    @Test
    public void testDivide() {
        assertEquals(2, calc.divide(4, 2));
    }
}

---

## Step 5: Run Tests

Navigate to the project directory:

cd junit-demo

Run the tests using Maven:

mvn clean test

---

## Step 6: Expected Output

BUILD SUCCESS  
Tests run: 2, Failures: 0

---

## Outcome

- Maven project is configured successfully  
- JUnit test cases are created  
- Tests are executed using Maven  
- Basic understanding of build tools is achieved  
