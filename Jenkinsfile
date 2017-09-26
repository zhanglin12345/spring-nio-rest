#!groovy
@Library('jenkins-pipeline-shared-library-example')
import com.codependent.jenkins.pipelines.Utils

pipeline {
  agent any
  tools { 
    maven 'M3' 
    jdk 'JDK8' 
  }
  environment {
    utils = new Utils()
  }
  stages {
    stage ('Build Application') {
      steps {
        echo 'Building application'
        utils.hello('Codependent')
        sh '''
           echo "PATH = ${PATH}"
           echo "M2_HOME = ${M2_HOME}"
           ''' 
        sh 'mvn -Dmaven.test.failure.ignore=true clean install -U'
      }
    }
    stage ('Finish') {
      steps {
        echo 'Finishing application'
      }
    }
  }
}
