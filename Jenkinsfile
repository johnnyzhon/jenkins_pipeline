pipeline {
    agent {
        node {
                label 'docker'
        }
    }
    stages {
        stage('check_confilt') {
            steps {
                echo 'enter into confilt check'
            }
        }
        stage('prepare_env') {
            steps {
                echo 'enter into prepare env'
            }
        }
        stage('run_test') {
            steps {
                echo 'enter into test stage'
            }
        }
    }
}
