//CODE_CHANGES = getGitChanges()

pipeline {

    agent any
    tools {
        maven 'Maven'

    }
    parameters {
        string(name: 'VERSION', defaultValue: '', description: 'version to deploy on prod')
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
    environment {
        NEW_VERSION = '1.3.0'
        SERVER_CREDENTIALS = credentials('server-credentials')
    }

    stages {
        
        

        stage("build") {
  //          when {
  //              expression {
  //                  BRANCH_NAME == 'dev' && CODE_CHANGES == true
                }
            

            steps {
                script {

                }
                echo 'building the application...'
                echo 'Application built'
                echo "building version ${NEW_VERSION}"
                sh "mvn install"
            }
        

    stage("test") {
   //     when {
   //         expression {
   //             BRANCH_NAME == 'dev'
                  params.executeTests
            }
                    
            steps {
                echo 'testing the application...'

            }
        

    stage("deploy") {
            
            steps {
                echo 'deploying the application...'
    //            echo "deploying with ${SERVER_CREDENTIALS}"
    //            sh "${SERVER_CREDENTIALS}"
    // Below is the Wrapper Syntax
                withCredentials([
                    usernamePassword(credentials: 'server-credentials', usernameVariable: USER, passwordVariable: PWD)
                ]) {
                    sh "some script ${USER} ${PWD}"

                }
                echo "deploying version ${params.VERSION}"
            }
        }
    }
    post {
        always {
            //
        }
        success {
            //
        }
        failure {
            //
        }
    }
}