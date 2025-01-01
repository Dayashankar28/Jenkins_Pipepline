// @Library('myfirstlib') _
// pipeline {
//     agent any
//     stages {
//         stage('Checkout') {
//             steps {
//             //     script {
//             //     def config = [
//             //         url : 'https://github.com/Dayashankar28/Jenkins_Pipepline.git',
//             //         credId : 'gitcred',
//             //         branch : 'main'
//             //     ]
//             //     gitCheckout(config)
//             // }

//             sh ' echo hi '
//             sh ' echo Daya '
//             sh ' echo Shankar '
//             sh ' echo Ranju '
//             }
//         }
//     }
// }

pipeline{
    agent { label 'master' }
    stages{
        stage('Build'){
            steps{
                echo 'Bulid stage'
                sh 'sleep 10'
            }
        }
        stage('Test'){
            steps{
                echo 'Test stage'
                sh 'sleep 10'
            }
        }
        stage('Deploy'){
            steps{
                echo 'Deploy stage...'
            }
        }
    }
}