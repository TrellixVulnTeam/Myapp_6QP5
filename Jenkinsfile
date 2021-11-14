pipeline {
	agent any
	stages{

		stage('clone and clean repo'){
			steps {
				cleanWs()
				sh "git clone -b master https://github.com/arthking17/Myapp.git"
			}
		}

		stage('Build')
		{
			steps{
				script{
					sh "ansible-playbook Myapp/ansible/build.yml -i Myapp/ansible/inventory/host.yml"
				}
			}
		}
		
		stage('docker')
		{
		  steps{
		    script{
		      sh "ansible-playbook Myapp/ansible/docker.yml -i Myapp/ansible/inventory/host.yml"
		    }
		  }
		}

    stage('dockerhub') 
    {
     steps{
       script{
         sh "ansible-playbook Myapp/ansible/register.yml -i Myapp/ansible/inventory/host.yml"
       }
      }
    }
    
    stage ('Email Notification') 
    {
      steps {
        mail bcc: '', body: 'your pipeline has been built', cc: '', from: '', replyTo: '', subject: 'Build', to: 'arthurwilliam.ngassanguesseu@esprit.tn'
      }
    }

	}
}
