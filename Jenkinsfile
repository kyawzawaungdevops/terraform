pipeline {
agent any

stages{
  stage('Terraform Init'){
    steps {
	    script {
            sh 'terraform init'
        }
    }
  }
  stage('Terraform Plan'){
    steps {
	    script {
            sh 'terraform plan'
        }
    }
  }
  stage('Approval'){
    when { branch 'main'}
    steps {
       script {
          waitUntil {
            fileExists('dummyfile')
          }
       }
     }
   }
   stage('Terraform Apply'){
     when { branch 'main'}
     steps {
 	    script {
             sh 'terraform apply -auto-approve'
         }
     }
   }
}
}
