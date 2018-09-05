pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                //build your gradle flavor, passes the current build number as a parameter to gradle
                sh "./gradlew clean assembleDebug -PBUILD_NUMBER=${env.BUILD_NUMBER}"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                //build your gradle flavor, passes the current build number as a parameter to gradle
                sh "./gradlew clean assembleRelease -PBUILD_NUMBER=${env.BUILD_NUMBER}"
            }
        }
        stage('Archive'){
          steps{
            //tell Jenkins to archive the apks
            archiveArtifacts artifacts: 'app/build/outputs/apk/*/*.apk', fingerprint: true
          }
        }
    }
}