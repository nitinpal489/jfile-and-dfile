pipeline {
    agent any

    stages {
        stage('Docker Build') {
            steps {
                sh '''
                sudo docker build -t 767243193153.dkr.ecr.ap-south-1.amazonaws.com/dehradun:latest:$BUILD_NUMBER .
                # login to ecr 
                aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 767243193153.dkr.ecr.ap-south-1.amazonaws.com
                #push the image to ecr 
                sudo docker push 767243193153.dkr.ecr.ap-south-1.amazonaws.com/dehradun:latest:$BUILD_NUMBER
                '''
            }
        }
        // stage('EKS Deploy') {
        //     steps {
        //         sh '''
        //         # helm 
        //         helm upgrade -i static-dev static -n dev --set image.tag=$BUILD_NUMBER
        //         '''

            }
        }
    }
}