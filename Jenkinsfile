node {
    def server = Artifactory.server('saritha.jfrog.io')
    def buildInfo = Artifactory.newBuildInfo()
    def rtMaven = Artifactory.newMavenBuild()
   
   stage('Code Checkout') { 
     git credentialsId: 'githubID', url: 'https://github.com/itrainjaquar/maven-examples.git'
     
    }
   stage('Build') {
    //withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.0') {
      //sh 'mvn clean compile'
       rtMaven.tool = 'Maven-3.6.0'
       rtMaven.run pom: 'pom.xml', goals: 'clean compile'
      //}
    }
   stage('Unit Test run') {
    //withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.0') {
     //sh 'mvn test'
       rtMaven.tool = 'Maven-3.6.0'
       rtMaven.run pom: 'pom.xml', goals: 'test'
      //} 
    }
   stage('Sonarqube analysis'){
      //withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
      //    sh 'mvn sonar:sonar \
        //  -Dsonar.projectKey=maven-example-jaquar \
          //-Dsonar.organization=itrainjaquar \
          //-Dsonar.host.url=https://sonarcloud.io \
          //-Dsonar.login=059cb525c6367049212917d911e5f503300e980e
    
      //}
  }
  stage("Quality Gate"){
          
    }
   stage('Artifactory Configuration') {
    rtMaven.tool = 'Maven-3.6.0' // Tool name from Jenkins configuration
        rtMaven.deployer releaseRepo: 'libs-release-local', snapshotRepo: 'libs-snapshot-local', server: server
        rtMaven.resolver releaseRepo: 'libs-release', snapshotRepo: 'libs-snapshot', server: server
        rtMaven.deployer.deployArtifacts = false // Disable artifacts deployment during Maven run
     
    }

    stage ('Install') {
        rtMaven.run pom: 'pom.xml', goals: 'install', buildInfo: buildInfo
     }
 
    stage ('Deploy') {
        rtMaven.deployer.deployArtifacts buildInfo
    }
        
    stage ('Publish build info') {
        server.publishBuildInfo buildInfo
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
