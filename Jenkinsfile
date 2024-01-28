
def ci_type = DEV_CI

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
       						choice(name: 'CHOICES', choices: ['one', 'two', 'three'], description: '') }
					
			       
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
