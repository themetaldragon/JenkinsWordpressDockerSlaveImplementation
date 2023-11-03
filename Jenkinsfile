pipeline {
      agent {
            docker {
                  label ''
            }
      }
      environment { 
   NAME = "abc"
   VERSION = "${env.BUILD_ID}"
   IMAGE = "${NAME}:${VERSION}"
}  
      stages {
                
          stage ('Build') {
               agent any  
               steps {
                      sh 'docker build -f Dockerfile -t ${NAME}:${VERSION} .'
                        }
              }
          stage ('Push') {
                agent any
                
                steps {
                      sh 'docker tag ${NAME}:${VERSION} localhost:5000/${NAME}:${VERSION}'
                      sh  'docker push localhost:5000/${NAME}:${VERSION}'
                     }
          }
      
    stage ('cleanup2') {
              agent any
              steps {
              sh 'docker rmi localhost:5000/${NAME}:${VERSION}'
              }
   }
      }
}
