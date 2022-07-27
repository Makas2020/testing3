
node {

    def mvnHome = tool 'Maven3'
    stage ("checkout") {
      git branch: 'master', credentialsId: 'Jenkins_change', url: 'https://github.com/Makas2020/Change.git'
    }
    
    stage ('build') {
       sh "${mvnHome}/bin/mvn clean install -f MyWebApp/pom.xml"
    } 
    stage ('Code Quality scan') {
       withSonarQubeEnv('Sonarqube1') {
       sh "${mvnHome}/bin/mvn -f MyWebApp/pom.xml sonar:sonar"
        }
   }
    
      stage ('Code coverage') {
       jacoco()
   }
