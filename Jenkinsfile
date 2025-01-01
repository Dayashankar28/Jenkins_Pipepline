@Library('myfirstlib') _
pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                def config = {
                    url : 'https://github.com/Dayashankar28/Jenkins_Pipepline.git',
                    credId : 'gitcred',
                    branch : 'main'
                }
                gitCheckout(config)
            }
        }
    }
}
