#!/usr/bin/env groovy

GOLANG_VERSION = "1.11"

pipeline {
    agent {
        //label "master"
        kubernetes {
            label 'sample-app'
            defaultContainer 'jnlp'
            yaml """
apiVersion: v1
kind: Pod
metadata:
labels:
  component: ci
spec:
  # Use service account that can deploy to all namespaces
  serviceAccountName: cd-jenkins
  containers:
  - name: golang
    image: golang:1.11
    command:
    - cat
    tty: true
  - name: gcloud
    image: gcr.io/cloud-builders/gcloud
    command:
    - cat
    tty: true
  - name: kubectl
    image: gcr.io/cloud-builders/kubectl
    command:
    - cat
    tty: true
"""
        }
    }

    stages {
        stage('test') {
                        // docker run --rm \
                        // -v ${workspace}:/go/src/github.com/monsterstrike/mb_server \
                        // -w /go/src/github.com/monsterstrike/mb_server \
                        // golang:${GOLANG_VERSION} \
                        // bash apps/entrypoint/test.sh
            steps {
                // ln -s `pwd` /go/src/sample-app
                // cd /go/src/sample-app
                container('golang'){
                    sh """
                    bash test.sh
                    """
                }
            }
        }
    }
}
