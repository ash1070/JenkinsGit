
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
                        			message: "Select a git tag",
                        			parameters: [choice(name: "git_tag", choices: ["dev_ci" , "prod_ci"], description: "Git tag")]
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
