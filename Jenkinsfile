pipeline{
    agent any
    stages{
        stage("artifacts example")
        {
          steps{
            echo "artifacts working"
            archiveArtifacts artifacts: 'output.txt', fingerprint: true
        }
    }
}
}
