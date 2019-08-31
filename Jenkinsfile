node {
   
   stage('Code Checkout') { 
     git credentialsId: 'githubID', url: 'https://github.com/situnsjs/maven-examples.git'
     
    }
   stage('Build') {
    withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.0') {
      sh 'mvn clean compile'
      }
    }
   stage('Unit Test run') {
    withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.0') {
     sh 'mvn test'
      } 
    }
   stage('Sonarqube analysis'){
     withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.0') {
      sh 'mvn sonar:sonar \
         -Dsonar.projectKey=maven-example-jaquar \
         -Dsonar.organization=situnsjs_ITrainmyself \
         -Dsonar.host.url=https://sonarcloud.io \
         -Dsonar.login=f34e20399daf8cb714ba0a54f8f368d6fcfc211c'  
       }  
    }
  stage("Quality Gate"){
          
    }
   stage('Package to Jfrog') {
    
    }
   
   stage('Deploy to Dev') {
     
    }
   stage('Automation Testing') {
     
    }
   stage('Deploy to Test') {
     
    }
   stage('Smoke Testing') {
     
    }
   stage('Deploy to Prod') {
     
    }
   stage('Acceptance Testing') {
     
    }
}
