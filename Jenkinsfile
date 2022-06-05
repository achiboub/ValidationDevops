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
        }
}