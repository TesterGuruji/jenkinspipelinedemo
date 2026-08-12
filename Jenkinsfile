pipeline {
agent any
stages {
    stage('Run JMeter Pipeline') {
        steps {
            sh '''
            /Users/vaibhavsrivastava/Downloads/apache-jmeter-5.6.3/bin/jmeter -n -t /Users/vaibhavsrivastava/Desktop/Training/Edureka-TCSTraining/Scripts/JMeterScripts/S01_AddBook_bookStoreapp-HTTPScriptRecorder.jmx -l test3.csv
            '''
        }
    }
}
}
