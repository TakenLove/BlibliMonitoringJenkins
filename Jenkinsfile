pipeline {
 agent {
   label 'monitoring-vm'
 }
 
 stages {
   stage ('Test Pipeline') {
     steps {
      echo "Show Docker"
      sh '''
        docker --version
        docker image ls
        docker container ls
        
        echo "You can do docker-compose, adn other command her!!"
      '''
     }
   }
   
   stage ('Deployment : Docker Compose And Load Balancer') {
     steps {
      sh '''
       docker-compose -f ./docker-compose-prom.yml up -d
      '''
     }
   } 

   stage ('Deploy: Show Docker Compose Result') {
     steps {
       sh '''
        docker-compose -f ./docker-compose-prom.yml ps
        docker container ls 
       '''
     }
   }

 }
}

