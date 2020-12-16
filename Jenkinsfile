pipeline {
    agent any

    parameters { choice(name: 'herramienta', choices: ['gradle', 'maven'], description: '') }
    stages {
        stage('Pipeline') {
            steps {
                script {
                    
                    echo params.herramienta

                    if (params.herramienta == 'gradle') {
                        load 'gradle.groovy'
                }else {
                     load 'maven.groovy'
                    }
                }
            }
        }
    }
}
