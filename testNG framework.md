# TestNG framework

**Topics**

1. Introduction
  
2. What is TestNG
  
3. Advantages of TestNG over junit
  
4. Installation of TestNG
  
5. Some TestNG jar files
  
6. how to setup project with TestNG.
  
7. Create First TestNG class
  
8. TestNG annotations.
  
9. TestNG Internal order structure.
  
10. TestNG methods.
  
11. TestNG parameter.
  
12. TestNG Dataprovider.
  
13. TestNG priority.
  
14. Demostrated One selenium example
  
15. Example with selenium with webdrivermanger.
  
16. run test with maven commandline.
  

## Introduction

TestNG is a advance testing framework for writing test cases in java. it also allow us to write automated test case (testging suit.)

It's overcome the limitation of junit framework. it also provide some new annotation which make easy to write test cases.

## What is testNG

TestNG is a advance testing framework for writing test cases in java. it also allow us to write automated test case (testging suit.)

It's overcome the limitation of junit framework. it also provide some new annotation which make easy to write test cases.

It have some similar annotation like junit but internal working of those annotations are different, also no need of static imports.

the name TestNG framework carries meaning of framework and NG stands for "Next Generation" .

## Advantage of testNG

1. TestNG provide full control over the test cases.
  
2. It allow use to handle different pre-request at different stage of exection before running test case.
  
3. It generate the logs and HTML report of tests.
  
4. TestNG allow us group test cases in defferent catorgries like smoke, regression etc.
  
5. allow to run parallel test cases.
  
6. TestNG is open-source framework.
  
7. We can configure testing with xml config file.
  

## Installation of TestNG

1. **Install new software.**
  
  Open `install new software` option in eclipse, new windows will popup in that window click on add button, then it shows another small windows with two option - 1. Name and 2. url
  
  In name add - `TestNG`
  
  in url add - ` https://testng.org/testng-eclipse-update-site`
  
  then follow the steps like accepting licence and complete the installation.
  
2. **eclipse Marketplace.**
  
  Open `eclipse marketplace` option in help bar and after click it will open marketplace windows wait for loading and then seach for TestNG.
  
  and select TestNG with install button and procced with steps.
  

## TestNG jar files

To use Jar files directly in your project we need to download seperatly or if project is maven based then add the dependency in pom.xml file.

1. Manually download and add into project. (better for adding older version jar files.)
  
2. Add from the IDE. ( it will add latest version. )
  

## How to setup project with TestNG.

To Setup the project with TestNG It required to use xml file with contain configuration for running test.

1. adding TestNG dependency from IDE.
  
2. Adding testNG dependency in Maven.
  

## Create First TestNG class

To create Class for testing we have option available by which it reduce the code writing time.

developer must have to write testing code inside the `src/test/java` package.

## TestNG annotations.

1. **@BeforeSuite** - this will run before all tests executing in this suite (collection of different multiple tests cases.)
  
2. **@AfterSuite** - this will run after all tests executed in this suite.
  
3. **@BeforeTest** - this will execute before any test method belongs to the classes inside the tag is run.
  
4. **@AfterTest** - this will execute after any test method belongs to the classes inside the tag have run.
  
5. **@BeforeGroups** - This list of groups that this configuration method will run before first test method of that group. like smoke, regression.
  
6. **@AfterGroups** - This list of groups that this configuration method will run after last test method. like smoke of that group. like smoke, regression.
  
7. **@BeforeClass** - this will run before first test method in the current class is invoked.
  
8. **@AfterClass** - this will run after last test method in the current class have been run.
  
9. **@BeforeMethod** - this will run before each test method.
  
10. **@AfterMethod** - this will run after each test method.
  
11. **@Test** - this will contain main logic of testing which generate result of test.
  

## TestNG methods

**enabled** -- allow to disable or enable any test method so it will skip executions if that method set to false.

**dependsOnGroups** -- The list of groups on which current method depends.

**dependsOnMethods** -- The list of methods on which current method depends.

**groups** -- the list of groups this class/method belong to.

## TestNG parameter.

@Parameters: Descibes how to pass different value as parameter to a @Test method.

value - The list of variable used to fill the parameters of this method.

## TestNG Dataprovider.

The *DataProviders* in TestNG are another way to pass the parameters in the test function, the other one being TestNG parameters.

syntex

```java
	@DataProvider(name="name of data provider")
	public Object[][] methodname(){
		return new Object[][] {Add your data here};
	}
```

## TestNG priority.

Priority method is the way to execute the test in specific order based on intergers values.

By default all the test priorites are set to zero.

**rules of priority**

should be an int type

should be in -ve to +ve range.

if priority is set to 0 then it follow the alphabetical order.

## run test with maven commandline.

To run test with maven commandline first need to install maven into your system and then need to add two more plugins in pom.xml of the project.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">

    ...

    <dependencies>
    ...
    </dependencies>

    <build>
        <pluginManagement>
            <plugins>
                <plugin>
                    <artifactId>maven-compiler-plugin</artifactId>
                    <version>3.8.0</version>
                </plugin>
                <plugin>
                    <artifactId>maven-surefire-plugin</artifactId>
                    <version>2.22.1</version>
                    <configuration>
                        <suiteXmlFiles>testng.xml</suiteXmlFiles>
                    </configuration>
                </plugin>
            </plugins>
        </pluginManagement>
    </build>
</project>
```

then to execute test we have two commands

1. mvn test
  
2. mvn clean test
  

To run different test cases with different test files we need to make small changes into maven-surefire-plugin

````xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">

    ...

    <dependencies>
    ...
    </dependencies>

    <build>
        <pluginManagement>
            <plugins>
                ...
                <plugin>
                    <artifactId>maven-surefire-plugin</artifactId>
                    <version>2.22.1</version>
                    <configuration>
                        <suiteXmlFiles>${filename}</suiteXmlFiles>
                    </configuration>
                </plugin>
            </plugins>
        </pluginManagement>
    </build>
</project>
````

after this change we can execute test by passing the xml file name into mvn command.

```bash
mvn clean test -Dfilename=smoketestng.xml
mvn clean test -Dfilename=testng.xml
```
