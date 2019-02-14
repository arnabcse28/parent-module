# parent-module

We have created a set of sharable and portable maven module to demonstrate the issue that we are still facing. Sharing here those modules and all relevant information so that this can be simulated at your end.

- This demo consists of 5 modules as follows (attachment: maven-dependency-trigger-demo.tar): 
 - parent-module: this is parent module for rest of the modules (packaging type "pom") and needs to be built & published at first. 
 - low-level-module-1 and low-level-module-2: these are low level modules and doesn't have any dependency, other than parent-module as the parent. 
 - middle-level-module-1: depends on low-level-module-1 and low-level-module-2. 
 - top-level-module: depends on middle-level-module-1. That is it has transitive dependency to low-level-module-1 and low-level-module-2.

- Local Nexus instance is used at localhost:8081. Nexus hosted repositories are "Snapshots" and "Releases".

- Jenkinsfile in each repo executes the deploy goal using "withMaven(mavenSettingsConfig: 'local-nexus')". local-nexus setting.xml to be configured on the Jenkins. Nexus creds are the default ones: admin/admin123.

- Sample settings.xml is included as a resouce in this repo.
