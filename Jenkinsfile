pipeline {
  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'git@github.com:hsshin0602/source-maven-java-spring-hello-webapp.git'
       }
    }
    stage('Build') {
      steps {
          sh 'mvn clean package'
       }
    }
    stage('Deploy') {
      steps {
        sh 'scp /var/lib/jenkins/workspace/maven_project/target/hello-world.war ubuntu@172.31.47.106:/var/lib/tomcat9/webapps'
       }
    }
  }
}    
