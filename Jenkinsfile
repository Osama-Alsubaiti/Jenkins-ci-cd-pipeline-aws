node {
    stage('Clone Repo') {
        git credentialsId: 'GIT-Credentials', 
            url: 'https://github.com/Osama-Alsubaiti/maven-web-app.git'
    }

    stage('Maven Build') {
        def mavenHome = tool name: "Maven-3.9.4", type: "maven"
        def mavenCMD = "${mavenHome}/bin/mvn"
        sh "${mavenCMD} clean package"
    }

    stage('SonarQube Analysis') {
        withSonarQubeEnv('Sonar-Server-9.9') {
            def mavenHome = tool name: "Maven-3.9.4", type: "maven"
            def mavenCMD = "${mavenHome}/bin/mvn"
            sh "${mavenCMD} sonar:sonar"
        }
    }

    stage('Nexus Upload') {
        nexusArtifactUploader artifacts: [[
            artifactId: '01-Maven-Web-App', 
            classifier: '', 
            file: 'target/maven-web-app.war', 
            type: 'war'
        ]], 
        credentialsId: 'Nexus-Credentials', 
        groupId: 'in.ashokit', 
        nexusUrl: '65.2.169.151:8081', 
        nexusVersion: 'nexus3', 
        protocol: 'http', 
        repository: 'ashokit-snapshot-repository', 
        version: '1.0-SNAPSHOT'
    }

    stage('Deploy') {
        sshagent(['Tomcat-Server-Agent']) {
            sh 'scp -o StrictHostKeyChecking=no target/maven-web-app.war ubuntu@15.206.172.155:/opt/tomcat/webapps'
        }
    }
}
