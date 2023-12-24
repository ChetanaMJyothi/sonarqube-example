node('tomcat') {
    stage('Git Checkout Stage') {
        git branch: 'main', url: 'https://github.com/ChetanaMJyothi/sonarqube-example.git'
    }
    
    stage('Build Stage') {
        sh 'mvn clean install'
    }

    stage('SonarQube Analysis Stage') {
        withSonarQubeEnv('sonarQube') {
            sh "mvn clean verify sonar:sonar -Dsonar.projectKey=sonar-sonar"
        }
    }

    stage('Deploy') {
        sh 'sudo cp /home/ec2-user/workspace/sonar-proj/target/MyWebApp.war /opt/tomcat/webapps'
    }
}

