pipeline{
	agent any
	stages{
		stage('build'){
			steps{
				echo 'Building..'
				sh 'make'
				archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
				}
			}
		stage('test'){
			steps{
				echo 'Testing'
				sh 'make check || true' 
                junit '**/target/*.xml'
				}
			}
		stage('deploy'){
				when{
					expression {
						currentBuild.result == null || currentBuild.result == 'SUCCESS' 
					}
				}
				steps{
					echo 'Deploying'
					sh 'make publish'
				}
			}
		}
	}
}
