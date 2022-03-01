pipeline{
    agent any
    tools{
         jdk "JDK"
        gradle 'gradle' 
    }
    stages{
        stage("Clone"){
            steps{
             git branch: "main" , url:"https://github.com/iGom-ravi/Github_basixcs.git"
            }
        }
        stage("build"){
            steps{
                bat "gradlew.bat build"
            }
        }
        stage("artifacts example")
        {
          steps{
            echo "artifacts working"
            archiveArtifacts artifacts: '**/*.jar', fingerprint: true
        }
    }
}
}
