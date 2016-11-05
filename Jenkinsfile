node {
        def mvnHome
        stage('Preparation') {
                git 'git@github.com:BikeSyndikat/parent-pom.git'
                mvnHome = tool 'maven-3.3.9'
        }
        stage('Build') {
                if (isUnix()) {
                        sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
                }
        }
        stage('Results') {
                archive 'pom.xml'
        }
}
