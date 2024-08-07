@Library("shared-lib") _
pipeline { 
         agent { label "agent01" } 
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
                                    sh " docker build -t vishnu11/raviimage:1.0.0 ." 
                           }
                  }
                  stage (" store the image to dockerhub") {
                           steps { 
                                    sh " docker push vishnu11/raviimage:1.0.0"
                           }
                  }
         }}
                       
