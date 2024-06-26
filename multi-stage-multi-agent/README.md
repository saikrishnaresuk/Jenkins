# Multi Stage Multi Agent

Set up a multi stage jenkins pipeline where each stage is run on a unique agent. This is a very useful approach when you have multi language application
or application that has conflicting dependencies.

Pipeline
The pipeline block defines the entire Jenkins pipeline.

Agent
agent none: This means that the pipeline as a whole does not have a default agent. Each stage will specify its own agent.
Stages
The stages block contains multiple stage blocks, each representing a phase of the pipeline.

Stage: Back-end
stage('Back-end'): This defines a stage named "Back-end".

agent: Specifies that this stage should run inside a Docker container.

docker { image 'maven:3.8.1-adoptopenjdk-11' }: Uses the Docker image maven:3.8.1-adoptopenjdk-11, which is a Maven image with OpenJDK 11.
steps: Contains the steps to be executed in this stage.

sh 'mvn compile': Runs the Maven compile command in the shell, which compiles the Java project.
Stage: Front-end
stage('Front-end'): This defines a stage named "Front-end".

agent: Specifies that this stage should run inside a Docker container.

docker { image 'node:16-alpine' }: Uses the Docker image node:16-alpine, which is a lightweight Node.js 16 image based on Alpine Linux.
steps: Contains the steps to be executed in this stage.

sh 'npm install': Runs the npm install command in the shell, which installs the Node.js project dependencies.
Summary
The pipeline is divided into two stages: "Back-end" and "Front-end".
Each stage runs in a different Docker container specified by its agent.
The "Back-end" stage uses a Maven Docker image to compile a Java project.
The "Front-end" stage uses a Node.js Docker image to install project dependencies.
The agent none at the top level indicates that no agent is assigned to the entire pipeline, allowing each stage to define its own agent.






