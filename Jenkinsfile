pipeline{
    agent any

    stages{
    stage('Lint HTML') {
              steps {
                  'tidy -q -e *.html'
              }
         }
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