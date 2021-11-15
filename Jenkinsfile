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
