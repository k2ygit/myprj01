pipeline {
  agent { label 'jenkins-node' }

  triggers {
    pollSCM '* * * * *'
  }

  parameters {
    string defaultValue: 'k3zero', name: 'TOMCAT_USER_ID'
    string defaultValue: '192.168.202.131', name: 'TOMCAT_IP'
    string defaultValue: '/var/lib/tomcat9/webapps', name: 'TOMCAT_WEBAPP_DIR'
  }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/k2ygit/myprj01.git'
      }
    }

    stage('Maven Build') {
      tools { maven 'Maven-3' }
      steps {
        sh 'mvn clean package'
      }
    }

    stage('Deploy to Tomcat') {
      steps {
        sh "scp $(env.WORKSPACE)/target/hello-world.war ${params.TOMCAT_USER_ID}@${params.TOMCAT_IP}:${params.TOMCAT_WEBAPP_DIR}"
      }
    }
  }
}
