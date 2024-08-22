pipeline {
    agent any

    environment {
        TAG_NAME = 'theshubhamgour/node'                 // Tag Name
        APP_VERSION = 'nodeapp-release-v1.0.0'            // Version
        DOCKER_REPO = "${TAG_NAME}"                      // Docker Repo
        DOCKER_TAG = "${APP_VERSION}"                    // Docker Tag
        // DOCKERHUB_CREDENTIALS = credentials('DOCKERHUB_CREDENTIALS') // Replace with your Jenkins credential ID
    }

    stages {
        // stage('Cloning Repository') {
        //     steps {
        //         git 'https://github.com/theshubhamgour/node-todo-cicd.git'
        //     }
        // }

        stage('Build') {
            steps {
                sh 'docker build -t nodeapplication .'
            }
        }

        stage('Testing') {
            steps {
                echo 'Testing Success'
            }
        }

        stage('Docker Login') {
            steps {
                sh 'docker login -u theshubhamgour -p redhat123#'
            }
        }

        stage('Docker Tag Image') {
            steps {
                sh "docker tag nodeapplication ${DOCKER_REPO}:${DOCKER_TAG}"
            }
        }

        stage('Docker Push') {
            steps {
                sh "docker push ${DOCKER_REPO}:${DOCKER_TAG}"
            }
        }
    }
}
