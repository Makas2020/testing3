
node {

    def mvnHome = tool 'Maven3'
    stage ("checkout") {
      git branch: 'main', url: 'https://github.com/Makas2020/testing3.git'
    }
    
    stage ('build') {
       sh "${mvnHome}/bin/mvn clean install -f MyWebApp/pom.xml"
    } 
    stage ('Code Quality scan') {
       withSonarQubeEnv('Sonar20') {
       sh "${mvnHome}/bin/mvn -f MyWebApp/pom.xml sonar:sonar"
        }
   }
    
      stage ('Code coverage') {
       jacoco()
   }
}
