pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/Carrofle-Dang/nginx.git', branch: 'main'
      }
    }
    stage('deploy kubernetes') {
      steps {
        sh '''
        kubectl create deployment nginx --image=192.168.0.10:5000/multi-img
        kubectl expose deployment nginx --type=LoadBalancer --port=8080 \
                                               --target-port=80 --name=nginx-svc
        '''
      }
    }
  }
}
