pipeline{
	agent any
	stages{
	stage('git-clone'){
      steps{
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-id', url: 'https://github.com/MosesOrganization/multi-branch.git']]])
      }
    }
		stage('parallel-level'){
			parallel {
				stage('sub-job1'){
					steps{
						echo "sub-job1 task"
					}
				}
				stage ('sub-job2'){
					steps{
						echo "sub-job2 task"
					}
				}
			}
		}
		stage('version-check'){
			steps{
				echo "end of parallel job"
			}
		}
		stage('webhook-fix'){
			steps{
			  echo "webhook fix"
			  }
			}
			stage('2 parallel'){
				parallel{
					stage('to-test-multi-build'){
						steps{
							sh 'lscpu'
						}
					}
				}
			}
	}
}

