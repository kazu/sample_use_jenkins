#!/usr/bin/env groovy

GOLANG_VERSION = "1.11"

pipeline {
    agent {
        label "master"
    }

    stages {
        stage('test') {
            steps {
                bash test.sh
            }
        }
    }
}
