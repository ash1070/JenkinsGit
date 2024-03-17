
def ci_type = "dev_ci"

pipeline {
    agent none
    stages {
	
	stage('Select input') {
	    
        steps {

		script{
			
			git url: 'https://github.com/ash1070/jenkinsGit2.git'
			GIT_COMMIT_EMAIL = sh (
			    script: 'git branch -a | grep remotes > ${WORKSPACE}/branchesList.txt',
			    returnStdout: true
			).trim()
			
			echo "Git committer email: ${GIT_COMMIT_EMAIL}"
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
                    
                    steps {
				echo "$ci_type"
			}
                }
            }
        }
    }
}
