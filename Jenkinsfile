pipeline{
    agent any

    stages{
      stage('Build') {
              steps {
                  sh 'echo "Hello World"'
				  sh '''
					echo "multiline shell scripts work too"
					ls -lah
					'''
              }
         }

    }
} 