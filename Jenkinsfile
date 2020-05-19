pipeline{
    agent any
    
    stages{
      stage('Lint HTML') {
              steps {
                  sh 'tidy -q -e *.html'
              }
         }
        stage('Upload to AWS') {
              steps {
                  retry(3){         
                    withAWS(region:'us-east-2',credentials:'aws-static') {
                    sh 'echo "Uploading content with AWS creds"'
                        s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'mycicdjenkins',path:'path/to/target/file.txt')
                    }
                  }
              }
         }
         stage('Check if site is up') {
              steps {
                  retry(3){
                      sh 'curl -X GET "http://mycicdjenkins.s3-website.us-east-2.amazonaws.com/index.html"'
                  }
              }
         }
    }
}
