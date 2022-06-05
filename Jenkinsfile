pipeline {
    agent any
        stages {
            stage('Pull') {
                steps {
                    script {
                        checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                            userRemoteConfigs: [[
                                credentialsId:'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',
                                url: 'https://github.com/achiboub/ValidationDevops'
                            ]]])
                    }
                }
            }
            stage('build') {
                steps {
                    script {
                        sh 'npm install'
                        sh 'ansible-playbook ansible/build.yml -i ansible/inventory/host.yml '
                    }
                }
        }
        stage ('docker') {
                steps {
                    sh 'ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml'
                }
        }
        }
}