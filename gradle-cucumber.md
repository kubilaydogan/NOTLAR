```java
task cucumberTest(type: JavaExec) {
    dependsOn assemble, compileTestJava  // Ensures your code is compiled before running Cucumber tests.
    
    main = "io.cucumber.core.cli.Main"   // This is the main entry point for Cucumber.
    classpath = sourceSets.test.runtimeClasspath // Use the test runtime classpath, which includes Cucumber and test dependencies.

    args = [
        '--plugin', 'pretty',  // Format the test output to be human-readable.
        '--glue', 'com.example.steps',  // Specify the package where step definitions are located.
        'src/test/resources/features'   // Path to your feature files.
    ]
}
```
