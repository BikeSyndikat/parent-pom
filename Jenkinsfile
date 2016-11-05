node {
        stage('Stage Name') {
            env.PATH = "${tool 'maven-3.3.9'}/bin:${env.PATH}"
        }

        // Mark the code checkout 'stage'....
        stage('Checkout') {
        // checkout scm
        properties([[$class: 'GithubProjectProperty', displayName: '', projectUrlStr: 'https://github.com/BikeSyndikat/parent-pom/'], pipelineTriggers([])])
        // Get some code from a GitHub repository
        git branch: 'develop', credentialsId: 'nelbrechtgithub', url: 'git@github.com:BikeSyndikat/parent-pom.git'
        // Clean any locally modified files and ensure we are actually on origin/master
        // as a failed release could leave the local workspace ahead of origin/master
        sh "git clean -f && git reset --hard origin/develop"
        
        def mvnHome = tool 'maven-3.3.9'
        // we want to pick up the version from the pom
        def pom = readMavenPom file: 'pom.xml'
        }
        // Mark the code build 'stage'....
        stage('Build') {
        // sh 'mvn clean package'
        sh "${mvnHome}/bin/mvn clean deploy site-deploy"
        }
}
