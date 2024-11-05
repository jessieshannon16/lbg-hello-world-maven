pipeline {
    agent any
 
    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }
 
    stages {
        stage('Checkout') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'main', url: 'https://github.com/jessieshannon16/lbg-hello-world-maven.git'
 
                // Run Maven on a Unix agent.
                //sh "mvn -Dmaven.test.failure.ignore=true clean package"
 
                // To run Maven on a Windows agent, use
                // bat "mvn clean compile"
            }

            //post {
            //    // If Maven was able to run the tests, even if some of the test
            //    // failed, record the test results and archive the jar file.
            //    success {
            //        junit '**/target/surefire-reports/TEST-*.xml'
            //        archiveArtifacts 'target/*.jar'
            //    }
            //}
        }
        stage('Compile'){
                steps{
                    sh 'mvn clean compile'
                }
            }
        stage('Test') {
            steps {
                sh "mvn test"
            }
        }
        stage('Package'){
            steps{
                sh "mvn -Dmaven.test.skip package"
            }
        }
    }
}