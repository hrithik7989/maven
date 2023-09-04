pipeline
{
    agent any
    stages
    {
        stage('ContDownload')
        {
            steps
            {
                git 'https://github.com/hrithik7989/new.git'
            }
        }
        stage('ContBuild')
        {
            steps
            {
               sh 'mvn package' 
            }
        }
        stage('ContDeploy')
        {
            steps
            {
               deploy adapters: [tomcat9(credentialsId: '2d5228c2-2709-4ac7-995d-d82035dc3c74', path: '', url: 'http://172.31.21.216:8080')], contextPath: 'Testapp1', war: '**/*.war'
            }
        }
        stage('ContTesting')
        {
            steps
            {
              git 'https://github.com/hrithik7989/test.git'
              sh 'java -jar  /var/lib/jenkins/workspace/Dcpipeline/testing.jar'
            }
        }
        stage('ContDelivery')
        {
            steps
            {
               deploy adapters: [tomcat9(credentialsId: '2d5228c2-2709-4ac7-995d-d82035dc3c74', path: '', url: 'http://172.31.24.104:8080')], contextPath: 'prodapp1', war: '**/*.war' 
            }
        }
    }
}
