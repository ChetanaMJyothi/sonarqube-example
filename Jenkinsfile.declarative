pipeline{
    agent {label 'tomcat'}
    stages{
       stage('Git Checkout Stage'){
            steps{
                git branch: 'main', url: 'https://github.com/ChetanaMJyothi/sonarqube-example.git'
            }
         }        
       stage('Build Stage'){
            steps{
                sh 'mvn clean install'
            }
         }
        stage('SonarQube Analysis Stage') {
            steps{
                withSonarQubeEnv('sonarQube') { 
                    sh "mvn clean verify sonar:sonar -Dsonar.projectKey=sonar-sonar"
                }
            }
        }
        stage('Deploy'){
            steps{
                sh 'sudo cp /home/ec2-user/workspace/sonar-proj/target/MyWebApp.war /opt/tomcat/webapps'
            }
         }
    }
}
