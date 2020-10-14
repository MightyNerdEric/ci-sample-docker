// SPDX-License-Identifier: EPL-1.0
//
// Copyright (c) 2020 The Linux Foundation and others.
//
// All rights reserved. This program and the accompanying materials
// are made available under the terms of the Eclipse Public License v1.0
// which accompanies this distribution, and is available at
// http://www.eclipse.org/legal/epl-v10.html

def image

pipeline {
    agent {
        label 'centos7-docker-4c-2g'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    image = docker.build('ci-sample-docker')
                }
            }
        }
        stage('Docker Push') {
            steps {
                script {
                    docker.withRegistry("https://docker.io",
                                        "dockerhub-lfitsandbox") {
                        image.push("latest")
                    }
                }
            }
        }
    }
}
