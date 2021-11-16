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
