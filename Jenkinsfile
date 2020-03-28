pipeline {
    // agent {
    //     docker {
    //         image 'ruby'
    //     }
    // }
    agent any
    stages {
        // stage('Build') {
        //     steps {
        //         echo 'Building or resolve dependencies!'
        //         sh 'bundle install'
        //     }
        // }
        stage('Tests') {
            steps {
                echo 'Running regression tests'
                script {
                    try {
                        sh "cucumber -p ci"
                    } finally {
                        cucumber fileIncludePattern: '**/*.json', jsonReportDirectory: 'logs', sortingMethod: 'ALPHABETICAL'
                    }
                }
            }
        }
        // stage('Acceptance') {
        //     steps {
        //         echo 'Wait for acceptance by User'
        //         input(message: 'Go to production?', ok: 'Yes')
        //     }
        // }
        stage('Prod') {
            steps {
                echo 'WebApp is ready :)'
            }
        }
    }
}
