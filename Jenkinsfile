@Library('myfirstlib') _
pipeline {
    agent any
    environment{
        DOCKER_IMAGE_NAME='daya28/calculator'
        DOCKER_IMAGE_TAG='latest'
        DOCKERFILE_PATH='./Dockerfile'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                def config = [
                    url : 'https://github.com/Dayashankar28/Python_Flask_Calculator.git',
                    credId : 'gitcred',
                    branch : 'main'
                ]
                gitCheckout(config)
            }
            }
        }
        stage('Sonar_Scan'){
            steps{
                script{
                    withSonarQubeEnv('sonar_server') {
                                        sh """
                                        /opt/sonar-scanner/bin/sonar-scanner
                    """

                    }

                }
            }
        }

        stage('Docker_Build_Push'){

            steps{
                script{

                    gitDockerBuildPush( 
                                        DOCKER_IMAGE_NAME,
                                        DOCKER_IMAGE_TAG,
                                        DOCKERFILE_PATH,
                                        'dockerCredId'
                                        
                    )
                }
            }

        }

        stage('Scan Docker Image with trivey'){
            steps{
                script{
                    gittrivyScan(
                            DOCKER_IMAGE_NAME,
                            DOCKER_IMAGE_TAG
                    )
                }
            }
        }

        stage('Run Tests') {
    steps {

        script{

            try{
                sh 'python3 -m venv venv'
            sh '''#!/bin/bash
            source venv/bin/activate
            python -m unittest discover -s . -p "test_calc.py"
            '''
            }

            catch (Exception e){
                currentBuild.result = 'UNSTABLE'  // Set the build result to UNSTABLE
                echo "Test failed, but proceeding with the pipeline."
            }
            
        }
    }
}

    }

    post{
        always{
            publishHTML (target : [allowMissing: false,
                            alwaysLinkToLastBuild: true,
                            keepAll: true,
                            reportDir: '.',
                            reportFiles: 'report.html',
                            reportName: 'My_Cal_App_Reports',
                            reportTitles: 'My_Cal_App_Report']
                        )
            cleanWs()
        }
    }

}