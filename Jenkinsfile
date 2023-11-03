pipeline {
      agent {
            node {
                  label 'newnode'
            }
      }
      environment { 
   NAME = "abc"
   VERSION = "${env.BUILD_ID}"
   IMAGE = "${NAME}:${VERSION}"
}  
      stages {
                
          stage ('Build') {
               
               steps {
                      sh 'docker build -f Dockerfile -t ${NAME}:${VERSION} .'
                        }
              }
          stage ('Push') {
             
                
                steps {
                      sh 'docker tag ${NAME}:${VERSION} localhost:5000/${NAME}:${VERSION}'
                      sh  'docker push localhost:5000/${NAME}:${VERSION}'
                     }
          }
      
    stage ('cleanup2') {
              
              steps {
              sh 'docker rmi localhost:5000/${NAME}:${VERSION}'
              }
   }
      }
}
