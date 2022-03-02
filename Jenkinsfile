pipeline{
    agent any
    tools{
         jdk "JDK"
        gradle 'gradle' 
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
        stage("artifacts example")
        {
          steps{
            echo "artifacts working"
            archiveArtifacts artifacts: '**/*.war', fingerprint: true
        }
    }
}
}
