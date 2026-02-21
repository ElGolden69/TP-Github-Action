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

  }
}
