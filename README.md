# Jenkins_Notes Groovy 
Let's go through the 7-day plan to learn Jenkins Groovy:

Day 1: Introduction to Groovy

- Learn basic Groovy syntax and data types
- Understand how Groovy is used in Jenkins

Day 2: Jenkins Groovy Basics

- Learn about Jenkins Groovy scripts and their types (e.g., Script Console, Scriptler)
- Understand how to write and execute Groovy scripts in Jenkins

Day 3: Working with Jenkins Objects

- Learn about Jenkins objects (e.g., Job, Build, Node)
- Understand how to access and manipulate these objects using Groovy

Day 4: Groovy Scripting in Jenkins Pipelines

- Learn how to use Groovy in Jenkins pipelines
- Understand how to write pipeline scripts using Groovy

Day 5: Advanced Groovy Topics

- Learn about advanced Groovy topics (e.g., closures, metaprogramming)
- Understand how to apply these concepts in Jenkins Groovy scripts

Day 6: Practical Examples and Use Cases

- Learn through practical examples and use cases (e.g., automating builds, deployments)
- Understand how to apply Groovy scripting to real-world Jenkins scenarios

Day 7: Putting it all Together

- Review and practice what you've learned
- Work on a project that integrates Groovy scripting with Jenkins

Let's dive deeper into Day 1: Introduction to Groovy.

Groovy Syntax

Groovy's syntax is similar to Java's, but with some key differences:

- Semicolons are optional
- Type declarations are optional (dynamic typing)
- Groovy uses def for variable declarations

Data Types

Groovy supports the following data types:

- Strings (e.g., "hello")
- Numbers (e.g., 123, 3.14)
- Booleans (e.g., true, false)
- Lists (e.g., [1, 2, 3])
- Maps (e.g., [name: "John", age: 30])

Variables

In Groovy, you can declare variables using the def keyword:

- def name = "John"
- def age = 30

Operators

Groovy supports various operators for arithmetic, comparison, logical operations, and more:

- Arithmetic: +, -, *, /, %
- Comparison: ==, !=, >, <, >= , <=
- Logical: &&, ||, !

Practice Time!

Try writing some basic Groovy scripts to get familiar with the syntax. For example:

- Declare variables and print their values
- Perform arithmetic operations
- Use logical operators

Here's how you can write some basic Groovy scripts to get familiar with the syntax:

### **1. Declare Variables and Print Their Values**
```groovy
// Declaring variables
def name = "Jenkins"
def age = 5
def isActive = true

// Printing variable values
println "Name: ${name}"
println "Age: ${age}"
println "Is Active: ${isActive}"
```

**Explanation**:
- `def` is used to declare variables in Groovy.
- `${}` is used to interpolate variables within a string.

### **2. Perform Arithmetic Operations**
```groovy
// Arithmetic operations
def num1 = 10
def num2 = 5

def sum = num1 + num2
def difference = num1 - num2
def product = num1 * num2
def quotient = num1 / num2
def remainder = num1 % num2

// Printing results
println "Sum: ${sum}"
println "Difference: ${difference}"
println "Product: ${product}"
println "Quotient: ${quotient}"
println "Remainder: ${remainder}"
```

**Explanation**:
- Basic arithmetic operators like `+`, `-`, `*`, `/`, and `%` are used to perform operations.
- The results are stored in variables and then printed.

### **3. Use Logical Operators**
```groovy
// Logical operations
def isTrue = true
def isFalse = false

def andOperation = isTrue && isFalse
def orOperation = isTrue || isFalse
def notOperation = !isTrue

// Printing results
println "AND Operation: ${andOperation}"  // false
println "OR Operation: ${orOperation}"    // true
println "NOT Operation: ${notOperation}"  // false
```

**Explanation**:
- `&&` is used for the logical AND operation.
- `||` is used for the logical OR operation.
- `!` is used for the logical NOT operation.

### **Running the Script**

You can run these scripts directly in a Groovy console, or integrate them into a Jenkins pipeline to see them in action.

This exercise should help you get comfortable with the basic syntax and operations in Groovy.

Let's move on to Day 2: Jenkins Groovy Basics.

Jenkins Groovy Scripts

Jenkins provides several ways to execute Groovy scripts:

1. Script Console: Execute Groovy scripts directly in the Jenkins web interface.
2. Scriptler: Store and manage Groovy scripts for reuse.
3. Pipeline scripts: Use Groovy to write Jenkins pipeline scripts.

Script Console

1. Access the Script Console from the Jenkins web interface.
2. Write and execute Groovy scripts directly in the console.
3. Use the jenkins object to access Jenkins functionality.

Scriptler

1. Store Groovy scripts in the Scriptler repository.
2. Manage and organize scripts using tags and descriptions.
3. Execute scripts from the Scriptler repository.

Pipeline Scripts

1. Write Groovy scripts to define Jenkins pipelines.
2. Use the pipeline object to access pipeline functionality.
3. Execute pipeline scripts to automate build and deployment processes.

Practice Time!

Try executing a simple Groovy script in the Script Console. For example:

- Print the Jenkins version: println jenkins.version
- List all Jenkins jobs: jenkins.items.each { job -> println job.name }

Let's move on to Day 3: Working with Jenkins Objects.

Jenkins Objects

Jenkins provides various objects to interact with its components. Here are some key objects:

1. Job: Represents a Jenkins job.
2. Build: Represents a build of a job.
3. Node: Represents a Jenkins node (agent).
4. Executor: Represents an executor on a node.
5. Workspace: Represents the workspace of a job.

Accessing Objects

You can access these objects using Groovy scripts in Jenkins. Here are some examples:

- Get a job object: def job = jenkins.getItem('my-job')
- Get a build object: def build = job.getLastBuild()
- Get a node object: def node = jenkins.getNode('my-node')

Manipulating Objects

You can manipulate these objects using various methods, such as:

- job.scheduleBuild() to trigger a build
- build.getArtifacts() to get artifacts from a build
- node.createLauncher() to create a launcher on a node

Practice Time!

Here are some Groovy scripts that demonstrate how to access and manipulate Jenkins objects:

### **1. Get the Last Build of a Job and Print Its Result**
This script retrieves the last build of a specific Jenkins job and prints the result (e.g., SUCCESS, FAILURE).

```groovy
// Replace 'YourJobName' with the name of your job
def job = Jenkins.instance.getItemByFullName('YourJobName')

// Check if the job exists
if (job != null) {
    def lastBuild = job.getLastBuild()  // Get the last build
    
    if (lastBuild != null) {
        def result = lastBuild.getResult()  // Get the result of the last build
        println "Last build result for job '${job.name}': ${result}"
    } else {
        println "No builds found for job '${job.name}'"
    }
} else {
    println "Job not found!"
}
```

### **2. Trigger a Build of a Job**
This script triggers a new build of a specific Jenkins job.

```groovy
// Replace 'YourJobName' with the name of your job
def job = Jenkins.instance.getItemByFullName('YourJobName')

// Check if the job exists
if (job != null) {
    def queueItem = job.scheduleBuild2(0)  // Trigger the build with no delay (0 seconds)
    
    if (queueItem != null) {
        println "Build triggered for job '${job.name}'"
    } else {
        println "Failed to trigger build for job '${job.name}'"
    }
} else {
    println "Job not found!"
}
```

### **3. Get the Workspace of a Job and Print Its Contents**
This script accesses the workspace of the last build of a specific Jenkins job and prints the contents of the workspace directory.

```groovy
import hudson.FilePath

// Replace 'YourJobName' with the name of your job
def job = Jenkins.instance.getItemByFullName('YourJobName')

// Check if the job exists
if (job != null) {
    def lastBuild = job.getLastBuild()  // Get the last build
    
    if (lastBuild != null) {
        def workspace = lastBuild.getWorkspace()  // Get the workspace
        
        if (workspace != null) {
            println "Contents of the workspace for job '${job.name}':"
            
            // List and print the files in the workspace
            workspace.list().each { FilePath file ->
                println file.getName()
            }
        } else {
            println "Workspace not found for job '${job.name}'"
        }
    } else {
        println "No builds found for job '${job.name}'"
    }
} else {
    println "Job not found!"
}
```

### **Explanation of Key Concepts:**

1. **`Jenkins.instance.getItemByFullName('YourJobName')`**:
   - Retrieves a specific Jenkins job by its name.

2. **`getLastBuild()`**:
   - Gets the last build object of the job.

3. **`getResult()`**:
   - Returns the result of the build (e.g., SUCCESS, FAILURE, ABORTED).

4. **`scheduleBuild2(0)`**:
   - Triggers a new build of the job with no delay (`0` seconds).

5. **`getWorkspace()`**:
   - Returns the workspace (the directory where the job’s files are located) of the last build.

6. **`workspace.list()`**:
   - Lists the files and directories in the workspace.

### **Use Cases:**
- **Monitoring**: Automatically monitor and report the status of your Jenkins builds.
- **Automation**: Trigger builds programmatically as part of a larger automation process.
- **Workspace Management**: Inspect or manage files in the workspace, useful for debugging or automation.

These scripts provide a starting point for interacting with Jenkins objects using Groovy.

Let's move on to Day 4: Groovy Scripting in Jenkins Pipelines.

Groovy Scripting in Pipelines

Jenkins pipelines allow you to automate build, test, and deployment processes using Groovy scripts.

Pipeline Syntax

Pipeline scripts use a specific syntax:

- pipeline { ... } block defines the pipeline
- stages { ... } block defines the stages
- stage('Name') { ... } block defines a stage
- steps { ... } block defines the steps

Groovy in Pipelines

You can use Groovy code within pipeline scripts:

- Use script { ... } block to write Groovy code
- Access pipeline variables using env.VARIABLE_NAME
- Use sh step to execute shell commands

Example Pipeline Script

Here's an example pipeline script:

pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    def buildNumber = env.BUILD_NUMBER
                    println "Building ${buildNumber}"
                }
                sh 'make build'
            }
        }
        stage('Deploy') {
            steps {
                script {
                    def deployEnv = env.DEPLOY_ENV
                    println "Deploying to ${deployEnv}"
                }
                sh 'make deploy'
            }
        }
    }
}

Practice Time!

Try writing your own pipeline script using Groovy. For example:

- Create a pipeline with two stages: Build and Deploy
- Use Groovy code to print the build number and deploy environment
- Execute shell commands to build and deploy your application


