pipeline{
    agent {
        docker {
            image 'allbears/jenkins-android:1.0.1'
            args '-v $HOME/.gradle:/Users/ops/.jenkins/workspace/jenkins-android-sample_master/\?/.gradle/'
        }
    }
    stages {
        stage('Build'){
             steps {
                sh './gradlew clean && rm -rf ./app/build/'
                sh './gradlew assembleRelease'
             }
        }
       stage('UnitTest'){   
             steps {
                sh './gradlew test' 
             }
        }
        stage('Archive') {  
            steps {
                archiveArtifacts artifacts: 'app/build/outputs/**/*.apk', fingerprint: true  
            }
        }

    }
}
