pipeline
{
    agent any
    stages
    {
        stage('continuous download')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'

            }
        }
        stage('continuos build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('continuous deploy')
        {
            steps
            {
                sh 'scp /home/ubuntu/.jenkins/workspace/decpipeline/webapp/target/webapp.war ubuntu@172.31.23.14:/var/lib/tomcat9/webapps/Qaenv.war'
            }
        }
        stage('continous testing')
        {
            steps
            {
                git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
                sh 'java -jar /home/ubuntu/.jenkins/workspace/decpipeline/testing.jar'
                
            }
        }
        stage('continuous delivery')
        {
            steps
            {
                sh 'scp /home/ubuntu/.jenkins/workspace/decpipeline/webapp/target/webapp.war ubuntu@172.31.25.159:/var/lib/tomcat9/webapps/prodenv.war'

            }
        }
    }
}
