pipeline {
    agent any

    parameters { choice(name: 'herramienta', choices: ['gradle', 'maven'], description: '') }
    stages {
        stage('Pipeline') {
            steps {
                script {
                    
                    echo params.herramienta

                    env.STAGE=''

                    if (params.herramienta == 'gradle') {
                        def ejecucion = load 'gradle.groovy'
                        ejecucion.call()
                }else {
                     def ejecucion = load 'maven.groovy'
                        ejecucion.call()
                    }
                }
            }
        }
    }
    post {
        success {
            slackSend message: "Build Success: [Nicolas Hermosilla][${env.JOB_NAME}][${params.herramienta}] Ejecución exitosa."
        }
        failure {
            slackSend message: "Build Failure: [Nicolas Hermosilla][${env.JOB_NAME}][${params.herramienta}]] Ejecución fallida en stage [${env.STAGE}]"
        }
    }
}
