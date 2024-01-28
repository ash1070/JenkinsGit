
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
					
					parameters {
                    				choice(name: 'ci_vera', choices: ['DEV_CI' , 'PROD_CI'] , description: 'ci_veracode')
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
				echo "$ci_type"
			}
                }
            }
        }
    }
}
