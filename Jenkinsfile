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
        /Users/vaibhavsrivastava/Downloads/apache-jmeter-5.6.3/bin/jmeter -n -t S01_AddBook_bookStoreapp-HTTPScriptRecorder.jmx -l test2.csv -e -o v02dashboard
        """

        }
    }

    stage('Archive Results') {
        steps {
            archiveArtifacts artifacts: 'test2.csv'
            archiveArtifacts artifacts: 'v02dashboard/**'
        }
    }

    stage('Publish HTML Report') {
        steps {
            perfReport filterRegex: '', showTrendGraphs: true, sourceDataFiles: 'test2.csv'
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
