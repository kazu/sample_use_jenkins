#!/usr/bin/env groovy

GOLANG_VERSION = "1.11"

pipeline {
    agent {
        label "master"
    }

    stages {
        stage('test') {
            steps {
                sh """
                bash test.sh
                """
            }
        }
    }
}
