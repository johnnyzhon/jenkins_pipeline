def lastResult = "none"

pipeline {
    agent none
    options {
        timestamps()
        timeout(time: 1, unit: 'HOURS')
        buildDiscarder(logRotator(numToKeepStr: '10'))
        skipDefaultCheckout()
    }
    stages { 
        stage('prepare node') {
            agent { label "host" }
            steps {
                echo "enter into node prepare stage,request for test gw vlan id."
                sleep 5
            }
        }
        stage('run test') {
            agent { label "${WORKNODE}" }
            steps {
                echo 'enter into test stage.'
                script {
                    try {
                        timeout(time: 5, unit: 'MINUTES'){
                            sh 'python --version'
                            sleep 10
                        }
                    }
                    catch(ex){
                        echo 'continue for next stage.'
                        lastResult = "FAILURE"
                    }
                }
            }
            post {
                always {
                    echo "collect test result and report to server"
                }
            }
        }
        stage('release node') {
            agent { label "host" }
            steps {
                echo "enter into stage, clear worknode ${WORKNODE} vlan tag."
                sleep 5
            }
        }
    }
    post {
        always {
            script {
                if ("${lastResult}" == "FAILURE"){
                    echo "current result ${lastResult}"
                    currentBuild.result = "FAILURE"
                }
            }
            echo "send mail to receiver after pipeline done."
        }
    }
}
