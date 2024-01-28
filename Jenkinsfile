
def ci_type = "dev_ci"

pipeline {
    agent none
    stages {
	
	stage('Non-Parallel Stage') {
	    agent {
                        label "master"
                }
        steps {

		script{
			
		

			ci_type = input( 
					
					parameters { 
       						choice(name: 'veracode', choices: ['dev_ci', 'prod_ci', 'dev_ci'], description: '') }
					
			       
			       )
			}
		
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
				echo "$ci_type"
			}
                }
            }
        }
    }
}
