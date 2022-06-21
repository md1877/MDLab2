pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }
    environment{
       ArtifactId = readMavenPom().getArtifactId()
       Version = readMavenPom().getVersion()
       Name = readMavenPom().getName()
       GroupId = readMavenPom().getGroupId()
    }

    stages {
        // Specify various stage with in stages

        // stage 1. Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'

            }
        }
// stage 3
stage ('publish')
{
    steps {
        nexusArtifactUploader artifacts: [[artifactId: 'hello-world-maven', classifier: '', file: 'target/hello-world-maven-0.0.4-SNAPSHOT.war', type: 'war']], credentialsId: 'ffc3cbdc-d93c-481a-942f-89034cb4349e', groupId: 'io.happycoding', nexusUrl: '172.20.10.250:8081', nexusVersion: 'nexus2', protocol: 'http', repository: 'MD-DevOpsLab-Snapshot', version: '0.0.4-SNAPSHOT'
    }
}
        // Stage3 : deploy
        stage ('deploy'){
            steps {
               echo ' Deplying.....'

            }
        }


        // Stage 4 : Print some information
        stage ('Print Environment variables'){
                    steps {
                        echo "Artifact ID is '${ArtifactId}'"
                        echo "Version is '${Version}'"
                        echo "GroupID is '${GroupId}'"
                        echo "Name is '${Name}'"
                    }
                }

        
    }

}