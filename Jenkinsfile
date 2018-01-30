node('master') {
    def workSpaceHome = pwd()
    stage('Clean') {
        deleteDir()
    }
    stage('Checkout') {
        checkout scm
    }
    stage('Build') {
		echo workSpaceHome
		load(workSpaceHome + "/config.groovy")
		echo "loading done"
			if (isUnix()) {
				sh "mvn compile"
				sh "mvn package"
			}
			else{
				bat "mvn compile"
				bat "mvn package"
		   }	
    }
}