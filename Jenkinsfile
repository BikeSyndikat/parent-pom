node {
    // Mark the code checkout 'stage'....
    stage 'Checkout'
    // Get some code from a GitHub repository
    git branch: '', credentialsId: 'nelbrechtgithub', url: 'git@github.com:BikeSyndikat/parent-pom.git'
    // Clean any locally modified files and ensure we are actually on origin/master
    // as a failed release could leave the local workspace ahead of origin/master
    sh "git clean -f && git reset --hard origin/master"
    def mvnHome = tool 'maven-3.3.9'
    // we want to pick up the version from the pom
    def pom = readMavenPom file: 'pom.xml'
    // Mark the code build 'stage'....
    stage 'Build'
    sh "${mvnHome}/bin/mvn clean deploy site-deploy"
    // Now we have a step to decide if we should publish to production 
    // (we just use a simple publish step here)
}
