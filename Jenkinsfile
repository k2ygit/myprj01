pipeline {
  agent { label 'jenkins-node' }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/hsshin0602/source-maven-java-spring-hello-webapp.git'
      }
    }

    stage('Maven Build') {
      steps {
        sh 'mvn clean package'
      }
    }

    stage('Deploy to Tomcat') {
      steps {
        sh 'scp /var/lib/jenkins/workspace/maven_pipeline/target/hello-world.war ubuntu@172.31.47.106:/var/lib/tomcat9/webapps'
      }
    }
  }
}
