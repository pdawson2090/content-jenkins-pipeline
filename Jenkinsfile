pipeline{
	agent any
	stages{
		stage('build'){
			 steps{
				echo 'Building..'
				sh 'javac -d . src/*.java'
				sh 'echo Main-Class: Rectangulator > MANIFEST.MF'
				sh 'jar -cvmf MANIFEST.MF rectangle.jar *.class'
				archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
			}
	        }
		stage('test'){
			steps{
				echo 'Testing'
				sh 'true' 
        
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
					
				}
		}
	}
}

