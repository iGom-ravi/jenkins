pipeline{
    agent any
    tools{
         jdk "JDK"
        gradle 'gradle' 
        maven 'maven'
    }
    stages{
        stage("Clone"){
            steps{
             git branch: "main" , url:"https://github.com/iGom-ravi/springboot.git"
            }
        }
        stage("build"){
            steps{
                bat "mvn clean install"
            }
        }
        stage('tomcat checkout'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://localhost:9090')], contextPath: 'GomTest', onFailure: false, war: 'target/*.war'
            }
        }
        stage('SonarQube Analysis') {
     steps{
    withSonarQubeEnv('sonar') {
    bat 'mvn sonar:sonar'
    }
    }
    }
        stage("artifacts example")
        {
          steps{
            echo "artifacts working"
            archiveArtifacts artifacts: '**/*.war', fingerprint: true
        }
    }
}
}
