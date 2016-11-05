node {
        git url: 'git@github.com:BikeSyndikat/parent-pom.git'
        def mvnHome = tool 'maven-3.3.9'
        sh "${mvnHome}/bin/mvn -B clean deploy site-deploy"
}
