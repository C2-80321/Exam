pipeline {
    agent any

    stages {
        stage ('git repository') {
            steps {
                git branch: 'master', url: 'https://github.com/C2-80321/Exam.git'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker image build -t kiranshinde908/mywebsite .'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_5_1IJs3y_ZIPubfyoq4aFiKOif4 | /usr/bin/docker login -u kiranshinde908 --password-stdin'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push kiranshinde908/mywebsite'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm myservice1'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name myservice1 --replicas 5 -p 9876:80 kiranshinde908/mywebsite'
            }
        }
    }
}


