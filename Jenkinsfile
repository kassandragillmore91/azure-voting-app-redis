pipeline {
    agent {
        docker {
            image 'maven'
            args '--privileged -v $HOME/.m2:/home/jenkins/.m2 -ti -u 496 -e MAVEN_CONFIG=/home/jenkins/.m2 -e MAVEN_OPTS=-Xmx2048m'
        }
   }

   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }
      stage('Docker Build') {
        steps {
            sh 'docker images -a'
            sh '''
               cd azure-vote/
               docker images -a
               docker build -t jenkins-pipeline .
               docker images -a
               cd ..
               '''
        }
      }
   }
}