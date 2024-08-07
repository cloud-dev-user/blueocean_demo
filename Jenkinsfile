@Library("shared-lib") _
pipeline { 
         agent { label "agent01" } 
         parameters {
  string defaultValue: '1.0.0', description: 'This is docker tag to be assigned to newly generated docker image ', name: 'docker_tag'
}
         stages { 
                     stage("build my package") {
                       steps { 
                            javaBuild()
                       }
                     }
                  stage("Sonar scanning for SCA") {
                       steps { 
                            echo "this is sonar scanning" 
                       }
                     }
                  stage (" Creating Docker Image " )  {
                           steps{
                                    sh " cp target/my-app.war . && sudo docker build -t vishnu11/raviimage:$docker_tag ." 
                           }
                  }
                  stage (" store the image to dockerhub") {
                           steps { 
                                    sh " sudo docker push vishnu11/raviimage:$docker_tag"
                           }
                  }
                  stage ( " Run the docker container " ){
                       steps {
                                sh " sudo docker run -d -p 8081:8081 --name webapp1 vishnu11/raviimage:$docker_tag"
                       }
                  }
          }}
                       
