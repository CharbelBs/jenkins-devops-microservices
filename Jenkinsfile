/* Sripted Pipelines
node {
	stage('Build') {
		echo "Build"
	}
	stage('Test') {
		echo "Test"
	}
}
*/

// Declarative Pipelines

pipeline {
    //agent any
    agent {
        docker {
            image 'maven:3.6.3'
        }
    }


  stages {

     stage("Build Test"){
        steps{

           bat 'mvn --version'
           echo "Build Test"
        }

     }

     stage("UI Test"){
             steps{

                echo "UI Test"
             }
      }
     stage("Integration Test"){
             steps{

                echo "Build Test"
             }
      }
  }

  post {

    always{
       echo "i run always"
    }
    success{
       echo "Success run"
    }
    failure{
       echo "Failure run"
    }
   //unstable, changed,....
  }

}
