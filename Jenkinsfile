pipeline {
	agent any
node {
    stage 'Checkout'
    checkout scm

    stage 'Build'
	echo "PATH = ${PATH}"
        echo "M2_HOME = ${M2_HOME}"
      	buildStatus= sh returnStatus: true, script:"${M2_HOME}/bin/mvn clean package" 
      	echo "Build status : ${buildStatus}"

    stage 'Record JUnit Results'
	junit 'target/surefire-reports/*.xml'

    stage 'Record Jacoco Results'
	publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'target/site/jacoco', reportFiles: 'index.html', reportName: 'Code Coverage', reportTitles: ''])

} 
}
