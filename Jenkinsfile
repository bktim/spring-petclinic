pipeline {
   agent any

   stages {
      stage('Build') {
         steps {
            git 'https://github.com/bktim/spring-petclinic.git'

            sh 'mvn clean package'

            script {
               docker.build("spring-petclinic:${env.BUILD_ID}")
            }
         }
      }
      stage('Run container') {
         steps {
            sh "docker run -d -p 8081:8080 spring-petclinic:${env.BUILD_ID}"
         }
      }
   }
}
