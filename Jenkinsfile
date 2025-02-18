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

node {

  stages {

     stage("Build Test"){
        steps{

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

  }

}
