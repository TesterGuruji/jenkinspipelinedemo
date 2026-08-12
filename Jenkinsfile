pipeline {
agent any
stages {
    stage('Checkout Source Code') {
        steps {
            git branch: 'main',
                url: 'https://github.com/TesterGuruji/jmetertest.git'
        }
    }

    stage('Verify Files') {
        steps {
            sh 'pwd'
            sh 'ls -R'
        }
    }

    stage('Run JMeter Test') {
        steps {

            sh """
        /Users/vaibhavsrivastava/Downloads/apache-jmeter-5.6.3/bin/jmeter -n -t S01_AddBook_bookStoreapp-HTTPScriptRecorder.jmx -l test1.csv -e -o dashboard
        """

        }
    }

    stage('Archive Results') {
        steps {
            archiveArtifacts artifacts: 'test1.csv'
            archiveArtifacts artifacts: 'dashboard/**'
        }
    }

    stage('Publish HTML Report') {
        steps {
            publishHTML([
               reportDir: 'dashboard',
                reportFiles: 'index.html',
                reportName: 'JMeter HTML Report',
                keepAll: true,
                alwaysLinkToLastBuild: true,
                allowMissing: false,
                includes: '**/*'
            ])
        }
    }

}

post {

    always {
        echo "Pipeline Finished"
    }

    success {
        echo "Performance Test Passed"
    }

    failure {
        echo "Performance Test Failed"
    }

}

}
