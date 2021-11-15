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
					  url: 'https://github.com/ihebbchini/myapp.git']]])
			      }
		          }
		     }
		      stage('Build') {
			   steps{
			      script{
			      sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml "
			      }
		          }
		     }
	     }
	     }
