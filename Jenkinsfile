   pipeline
   {

		agent any
		  stages {
		      stage('Pull') {
			   steps{
			      script{
				  checkout([$class: 'GitSCM', branches: [[name: '*/master']],
				      userRemoteConfigs: [[
					  credentialsId: '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',
					  url: 'https://github.com/ihebbchini/myapp']]])
			      }
		          }
		     }
			stage('Build') {
                           steps{
                              script{
				sh " npm install && ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
				}
                          }
                     }
			stage('Docker') {
                           steps{
                              script{
                                sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml"
                                }
                          }
                     }
			stage('Docker-Registry') {
                           steps{
                              script{
                                sh "ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.yml"
                                }
                          }
                     }




	     }
	     }
