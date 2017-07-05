node {
    stage 'Checkout'
    checkout scm

    stage 'Build'
	def mvnHome = tool 'M3'
      	buildStatus= sh returnStatus: true, script:"${mvnHome}/bin/mvn clean package" 
      	echo "Build status : ${buildStatus}"

    stage 'Record JUnit Results'
	junit 'target/surefire-reports/*.xml'

    stage 'Record Jacoco Results'
	publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'target/site/jacoco', reportFiles: 'index.html', reportName: 'Code Coverage', reportTitles: ''])

} 
