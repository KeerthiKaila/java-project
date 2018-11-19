properties([pipelineTriggers([githubPush()])])
pipeline {
	agent any
	stages {
	stage('Unit Tests') {
	    steps {
		    sh 'ant -f test.xml -v'
		    junit 'reports/result.xml'
	    }
	}  
	stage('Build') {
            steps {
		 sh 'ant -f build.xml -v'
            }
	}
          stage('Deploy') {
            steps {
                 archiveArtifacts artifacts: 'dist/rectangle-${BUILD_NUMBER}.jar'
		 sh(" aws s3 cp dist/rectangle-${BUILD_NUMBER}.jar s3://keerthikaila-assignment9/rectangle-${BUILD_NUMBER}.jar")	
				
            }
		}
	}
}
