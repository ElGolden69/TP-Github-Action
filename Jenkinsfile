pipeline {
  agent any
  
  tools{
    maven 'maven'
    nodejs 'node'
  }

  stages{
    stage("clean up"){
      steps {
        deleteDir()
      }
    }
    stage("clone repo"){
      steps {
      sh "git clone https://github.com/NouraneZouabi/deploy-app-spring-angular.git"
      }
    }

    stage("Generate backend image"){
      steps {
       dir("deploy-app-spring-angular/springboot/app"){
        sh "mvn clean package"
        sh "docker build -t nouran10/springboot-app ."
        sh "docker push nouran10/springboot-app"
       }
      }
    }

    stage("Generate frontend image"){
      steps {
       dir("deploy-app-spring-angular/angular-app"){
        sh "docker build -t nouran10/angular-app ."
        sh "docker push nouran10/angular-app"
       }
      }
    }

    stage("Run docker compose "){
      steps {
       dir("deploy-app-spring-angular"){
        sh "docker compose down --volumes"
        sh "docker compose pull"
        sh "docker compose up -d "
       }
      }
    }

  }
}
