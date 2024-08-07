@Library("shared-lib") _
pipeline { 
         agent { label "agent01" } 
         stages { 
                     stage("build my package") {
                       steps { 
                            javaBuild()
                       }
                     }
         }}
                       
