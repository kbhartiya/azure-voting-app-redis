pipeline {
   agent any

   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }

   stage('Docker Build') {
      steps {
         pwsh(script: 'docker images -a')
         pwsh(script: """
            cd azure-vote/
            docker images -agent
            docker build -t jenkins-pipeline .
            docker images -agent
            cd ..
         """)
      }
   }    
   }
}

