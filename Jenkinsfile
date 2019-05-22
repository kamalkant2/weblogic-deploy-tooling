pipeline {
    agent {
        docker {
            image 'phx.ocir.io/weblogick8s/wdt/jenkins/slave:3.9-wls12213'
            args '-v /root/.m2:/root/.m2'
        }
    }
    tools {
        maven 'maven-3.6.0'
        jdk 'jdk1.8.0_201'
    }

    stages {
        stage ('Environment') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "JAVA_HOME = ${JAVA_HOME}"
                    echo "M2_HOME = ${M2_HOME}"
                    mvn --version
                    ls -al /root/.m2
                '''
            }
        }
        stage ('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
    }
}