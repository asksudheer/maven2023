pipeline
{
    agent any
    stages
    {
        stage ('ContDownload')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            
            }
        }
            stage ('ÇontBuild')
            {
                steps
                {
                    sh 'mvn package'
                }
            }
        stage('ContDeployment')
        {
            steps
            {
               deploy adapters: [tomcat9(credentialsId: 'e3836396-d207-478f-a050-b9a7475051be', path: '', url: 'http://172.31.17.112:8080')], contextPath: 'mytestapp', war: '**/**.war'
            }
        }
        stage('ContTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeLine/testing.jar'
            }
        }
        stage ('çontdelivery')
        {
            steps
            {
                input id: 'Vrtcs', message: 'Need Approval from Project Manager'
                deploy adapters: [tomcat9(credentialsId: 'e3836396-d207-478f-a050-b9a7475051be', path: '', url: 'http://172.31.31.142:8080')], contextPath: 'myprodapp', war: '**/**.war'
            }
        }
    }
}
