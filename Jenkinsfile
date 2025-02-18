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

     stage("Checkout"){
        steps{

           sh 'mvn --version'
           sh 'docker --version'
           echo "Build Test"
           echo "BUILD_ID - $env.BUILD_ID"
           echo "BUILD_URL - $env.BUILD_URL"
        }

     }

     stage("Compile"){
             steps{

                sh "mvn clean compile"
             }
      }

/*      stage("Test"){
                   steps{

                      sh "mvn test"
                   }
            }

     stage("Integration Test"){
             steps{

                echo "mvn failsafe:integration-test failsafe:verify"
             }
      }

      */

      stage("Package") {

         steps{
           sh "mvn package -DskipTests"
         }
      }

      stage("Build image"){
                   steps{

                      script{
                        dockerImage = docker.build("charbelbsaibess/currency-exchange-devops:${env.BUILD_TAG}")
                      }
                   }
      }

      stage("Push image"){
                         steps{

                            script{
                              docker.withRegistry("","dockerHub"){
                               dockerImage.push();
                               dockerImage.push('latest');
                              }
                            }
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
