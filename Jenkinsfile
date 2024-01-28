
def ci_type = DEV_CI

pipeline {
    agent none
    stages {
	
	stage('Non-Parallel Stage') {
	    agent {
                        label "master"
                }
        steps {

		ci_type = input( 
					message "select veracode sandbox type"
					parameters {
                    				choice(name: "ci_vera", choices: ["DEV_CI" , "PROD_CI"] , description: "ci_veracode")
                			}
					
			       
			       )
		
                echo 'This stage will be executed first'
		
                }
        }

	
        stage('Run Tests') {
            parallel {
                
                stage('Test On Master') {
                    agent {
                        label "master"
                    }
                    steps {
						echo "Task1 on Master"
			}
                }
            }
        }
    }
}
