pipeline{
    agent any
    
    stages{
	  stage('Lint HTML') {
              steps {
                  tidy -q -e *.html
              }
         }
      stage('Upload to AWS') {
               steps {
                  retry(3){         
                    withAWS(region:'us-east-2',credentials:'aws-static') {
                    sh 'echo "Uploading content with AWS creds"'
                        s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'mycicdjenkins')
                    }
                  }
              }
         }
        
    }
}