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
    agent any
    //agent { docker { image 'maven:3.6.3' } }

  environment{

      dockerHome = tool "myDocker"   //already configured in jenkins tool
      mavenHome = tool "myMaven"
      PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
  }

  stages {

     stage("Build Test"){
        steps{

           sh 'mvn --version'
           sh 'docker --version'
           echo "Build Test"
           echo "BUILD_ID - $env.BUILD_ID"
           echo "BUILD_URL - $env.BUILD_URL"
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
