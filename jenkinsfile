pipeline {
    agent any
     environment { 
        name = 'akshit'
    }
   parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        
        booleanParam(name: 'isMale', defaultValue: true, description: '')
        
        choice(name: 'CITY', choices: ['HYD', 'MUMBAI', 'BANGLORE'], description: 'Pick something')
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
            }
        }
        stage('env variables') {
             environment { 
                username = 'myusername' 
            }
            steps {
                sh 'echo "${BUILD_ID}"'
                sh 'echo "${name}"'
                sh 'echo "${username}"'
            }
        }
        stage('Parameters') {
            steps {
                sh 'echo "${BUILD_ID}"'
                sh 'echo "${name}"'
                sh 'echo "${PERSON}"'
            }
        }
        stage('Continue?') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
            steps {
                echo "Hello, ${PERSON}, nice to meet you."
            }
        }
        stage('Example') {
            steps {
                echo 'Hello World'
            }
        }
        
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
        failure { 
            echo 'failure'
        }
        success { 
            echo 'success'
        }
    }
}
