pipeline {
  agent any
  stages {
    // stage('Hashing images') {
    //   steps {
    //     script {
    //       env.GIT_HASH = sh(
    //         script: "git show --oneline | head -1 | cut -d' ' -f1",
    //         returnStdout: true
    //       ).trim()
    //     }

    //   }
    // }

    stage('Lint Dockerfile') {
      steps {
        script {
          docker.image('hadolint/hadolint:latest-debian').inside() {
            sh 'hadolint ./Dockerfile | tee -a hadolint_lint.txt'
            sh '''
lintErrors=$(stat --printf="%s"  hadolint_lint.txt)
if [ "$lintErrors" -gt "0" ]; then
echo "Errors have been found, please see below"
cat hadolint_lint.txt
exit 1
else
echo "There are no erros found on Dockerfile!!"
fi
'''
          }
        }

      }
    }

    // stage('Build & Push to dockerhub') {
    //   steps {
    //     script {
    //       dockerImage = docker.build("rubenrulz/capstone-bcrypt:${env.GIT_HASH}")
    //       docker.withRegistry('', dockerhubCredentials) {
    //         dockerImage.push()
    //       }
    //     }

    //   }
    // }

    stage('Build & Push to ECR') {
      steps {
        script {
          dockerImage = docker.build("rubenrulz/capstone-bcrypt:${BUILD_NO}")
          docker.withRegistry("https://361588996336.dkr.ecr.us-east-2.amazonaws.com", "aws-credentials") {
        docker.image("your-image-name").push()
      }
        }

      }
    }
    stage('Scan Dockerfile to find vulnerabilities') {
      steps {
        aquaMicroscanner(imageName: "rubenrulz/capstone-bcrypt:${BUILD_NO}", notCompliesCmd: 'exit 4', onDisallowed: 'fail', outputFormat: 'html')
      }
    }

    stage('Deploying to EKS') {
      steps {
        dir(path: 'k8s') {
          withAWS(credentials: 'aws-credentials', region: 'us-east-2') {
            sh 'pip3 install --upgrade --user awscli'
            sh 'aws eks --region us-east-2 update-kubeconfig --name ruben-eks-EKS-Cluster'
            sh 'export KUBECONFIG=/var/lib/jenkins/.kube/config'
            sh "cat app-deployment.yaml | sed 's/{{BUILD_NO}}/${BUILD_NO}/g' | KUBECONFIG=/var/lib/jenkins/.kube/config kubectl  apply -f -"
          }

        }

      }
    }

    stage('Cleaning Docker up') {
      steps {
        script {
          sh "echo 'Cleaning Docker up'"
          sh "docker system prune"
        }

      }
    }

  }
  environment {
    dockerhubCredentials = 'dockerhubCredentials'
    BUILD_NO = 1
  }
}