@Library("shared-lib") _
pipeline { 
         agent { label "agent01" } 
         parameters {
  string defaultValue: '1.0.0', description: 'This is docker tag to be assigned to newly generated docker image ', name: 'docker_tag'
  string defaultValue: '8081', description: 'This is docker container port to be assigned to newly generated docker image ', name: 'container_port'
}                

         environment {
  docker_registry = "vishnu11/raviimage"
  default_container_port = "8080"
  default_container_name = "webapp1"
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
                                    sh " cp target/my-app.war . && sudo docker build -t $docker_registry:$docker_tag ." 
                           }
                  }
                  stage (" store the image to dockerhub") {
                           steps { 
                                    sh " sudo docker push $docker_registry:$docker_tag"
                           }
                  }
                  stage ( " Run the docker container " ){
                       steps {
                                sh " sudo docker run -d -p $container_port:$default_container_port --name $default_container_name $docker_registry:$docker_tag"
                       }
                  }
          }}
                       
