// pipeline {
//
//     agent { node { label 'workstation' } }
//
//     environment {
//         SSH = credentials('SSH')
//     }
//
//     options {
//         ansiColor('xterm')
//     }
//
//     triggers { pollSCM('H/2 * * * *') }
//
//     parameters {
//             string(name: 'APP_INPUT', defaultValue: '', description: 'Just Input')
//        }
//
//     stages {
//         stage('Hello-1') {
//         input {
//             message "Should we continue?"
//             ok "Yes, we should."
//         }
//            steps {
//              echo 'Hello World'
//              sh 'env'
//              sh 'echo APP_INPUT - $APP_INPUT'
//            }
//         }
//        stage('Example Deploy') {
//            when {
//                branch 'production'
//            }
//            steps {
//                echo 'Deploying'
//            }
//        }
//     }
//     post {
//         always {
//             sh 'echo post'
//         }
//     }
// }
//

pipeline {
    agent any
    stages {
        stage('Non-Parallel Stage') {
            steps {
                echo 'This stage will be executed first.'
            }
        }
        stage('Parallel Stage') {
            failFast true
            parallel {
                stage('Branch A') {
                    agent {
                        label "for-branch-a"
                    }
                    steps {
                        echo "On Branch A"
                    }
                }
                stage('Branch B') {
                    agent {
                        label "for-branch-b"
                    }
                    steps {
                        echo "On Branch B"
                    }
                }
                stage('Branch C') {
                    agent {
                        label "for-branch-c"
                    }
                    stages {
                        stage('Nested 1') {
                            steps {
                                echo "In stage Nested 1 within Branch C"
                            }
                        }
                        stage('Nested 2') {
                            steps {
                                echo "In stage Nested 2 within Branch C"
                            }
                        }
                    }
                }
            }
        }
    }
}