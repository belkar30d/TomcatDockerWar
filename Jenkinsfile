pipeline {
     agent any
     stages {
          stage("Compile") {
               steps {
                    sh "/usr/bin/mvn compile"
               }
          }
          stage("Unit test") {
               steps {
                    sh "/usr/bin/mvn test"
               }
          }
     
    
stage("Deploy") {
     steps {
          sh "/usr/bin/mvn deploy"
     }
}
stage("Docker build") {
     steps {
      
          sh "docker build -t datta_tomcat ."
     }
}

stage("Deploy to staging") {
     steps {
          sh "docker stop wartomcat"
          sh "docker rm wartomcat"
          sh "docker run -d -it -v /var/lib/jenkins/workspace/warDeplyTomcat/target/:/usr/local/tomcat/webapps/ -p 8090:8080 --name wartomcat datta_tomcat"
     }
}

     }
  post {
     always {
          sh "echo 'I did It'"
     }
}
}
