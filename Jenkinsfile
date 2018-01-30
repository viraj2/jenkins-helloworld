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
		echo "${buildtarget}"
		echo "${buildversion}"
			if (isUnix()) {
				sh "mvn compile -Dbuild.version=${buildversion}"
				sh "mvn package -P ${buildtarget}"
			}
			else{
				bat "mvn compile -Dbuild.version=${buildversion}"
				bat "mvn package -P ${buildtarget}"
		   }	
    }
	stage('Copy') {
		if (isUnix()) {
			sh "cp target/helloworld.hpi helloworld.hpi"
		}
		else{
			bat "cp target\\helloworld.hpi helloworld.hpi"
		}
	}
	
}