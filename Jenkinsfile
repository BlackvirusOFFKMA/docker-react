pipeline{
    agent{
        none    
    }
    stages{
        stage("Build"){
            steps{
                sh 'docker build -t stephengrider/react-test -f ./client/Dockerfile.dev ./client'
            }
            post{
                always{
                    echo "======== Building ========"
                }
                success{
                    echo "======== Build successfully ========"
                }
                failure{
                    echo "======== Build failed ========"
                }
            }
        }
        stage("Test"){
            steps {
                sh 'docker run stephengrider/react-test npm test -- --coverage'
            }
            post{
                always{
                    echo "====++++ Running test cases ++++===="
                }
                success{
                    echo "====++++ Test successful ++++===="
                }
                failure{
                    echo "====++++ Test failed ++++===="
                }
            }
        }
        stage("Deploy"){
            post{
                always{
                    echo "======= No deploy now =========="
                }
            }
        }
    }
    post{
        always{
            echo "======== Running pipeline========"
        }
        success{
            echo "======== Build and test success ========"
        }
        failure{
            echo "======== Build and test failed========"
        }
    }
}