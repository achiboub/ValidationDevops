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
        }
}