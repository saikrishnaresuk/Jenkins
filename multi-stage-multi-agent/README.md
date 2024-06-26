# Multi Stage Multi Agent

Set up a multi stage jenkins pipeline where each stage is run on a unique agent. This is a very useful approach when you have multi language application
or application that has conflicting dependencies.

This Jenkinsfile defines a Jenkins pipeline with two stages: "Back-end" and "Front-end". Each stage runs inside a specific Docker container and performs a simple command to check the version of the tools used (mvn for Maven and node for Node.js).

Pipeline Block
pipeline: This block defines the entire Jenkins pipeline.
Agent Block
agent none: This indicates that there is no global agent assigned to the entire pipeline. Each stage will specify its own agent.
Stages Block
The stages block contains individual stage blocks, each representing a part of the pipeline.

Stage: Back-end
stage('Back-end'): This defines a stage named "Back-end".

agent: Specifies the execution environment for this stage.

docker { image 'maven:3.8.1-adoptopenjdk-11' }: Runs this stage inside a Docker container using the maven:3.8.1-adoptopenjdk-11 image, which includes Maven 3.8.1 and OpenJDK 11.
steps: Contains the commands to be executed in this stage.

sh 'mvn --version': Runs the mvn --version command in the shell, which outputs the version of Maven installed in the Docker container. This is often used to verify that the correct version of Maven is available.
Stage: Front-end
stage('Front-end'): This defines a stage named "Front-end".

agent: Specifies the execution environment for this stage.

docker { image 'node:16-alpine' }: Runs this stage inside a Docker container using the node:16-alpine image, which includes Node.js version 16 and is based on Alpine Linux (a lightweight Linux distribution).
steps: Contains the commands to be executed in this stage.

sh 'node --version': Runs the node --version command in the shell, which outputs the version of Node.js installed in the Docker container. This is often used to verify that the correct version of Node.js is available.
Summary
The pipeline has two stages: "Back-end" and "Front-end".
Each stage uses a different Docker container to provide the necessary environment.
The "Back-end" stage uses a Maven and OpenJDK 11 image to run Maven commands.
The "Front-end" stage uses a Node.js 16 image to run Node.js commands.
The steps in each stage simply check and print the version of the respective tools (mvn for Maven and node for Node.js), verifying that the Docker containers are set up correctly.
This setup is useful for ensuring that the correct environments are being used and can serve as a basis for more complex build and test processes in a CI/CD pipeline.






