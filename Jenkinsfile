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

	}
}
