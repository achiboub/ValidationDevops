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
        stage ('push to docker registry') {
                steps {
                    sh 'ansible-galaxy collection install community.docker'
                    sh 'ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.yml'
                }
        }
        }
}