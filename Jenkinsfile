@Library('myfirstlib') _
pipeline {
    agent any
    environment{
        DOCKER_IMAGE_NAME: 'daya28/calculator'
        DOCKER_IMAGE_TAG: 'latest'
        DOCKERFILE_PATH: './Dockerfile'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                def config = [
                    url : 'https://github.com/Dayashankar28/Jenkins_Pipepline.git',
                    credId : 'gitcred',
                    branch : 'main'
                ]
                gitCheckout(config)
            }
            }
        }

        stage('Docker_Build_Push'){

            steps{
                script{

                    gitDockerBuildPush( DOCKER_IMAGE_NAME,
                                        DOCKER_IMAGE_NAME,
                                        DOCKERFILE_PATH,
                                        'dockerCredId'
                    )
                }
            }

        }
    }
}
