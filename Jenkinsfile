pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    environment {
        packageVersion = ''
        nexusUrl = '172.31.9.236:8081'
    }
    options {
        timeout(time: 1, unit: 'HOURS') //it will allow to run this pipeline for 1 hour to execute
        disableConcurrentBuilds()  //this wont allow to run 2 builds at a time
    }
    parameters {
        string(name: 'version', defaultValue: '', description: 'What is the artifact version?')
        string(name: 'environment', defaultValue: 'dev', description: 'What is environment?')
        // booleanParam(name: 'Destroy', defaultValue: 'false', description: 'What is Destroy?')
        // booleanParam(name: 'Create', defaultValue: 'false', description: 'What is Create?')
    }

    //build 
    stages {
        stage('Deploy') {
            steps {
                sh """
                echo "version: ${params.version}"
                echo "environment: ${params.environment}"
                """
            }
        }
        
    }
      // post build
        post { 
        always { 
            echo 'I will always say Hello again!'
        }
        failure{
            echo 'this runs when pipeline is failed, used generally to sned alerts'
        }
        success{
            echo 'I will say hello when pipeline is success'
        }
    } // After pipeline directory must be deleted from pipeline using deldir()
}