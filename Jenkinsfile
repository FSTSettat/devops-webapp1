//START-OF-SCRIPT
//comment1
    node('agent1') {
        def RELEASENAME = "webapp"

        properties([
            pipelineTriggers([pollSCM('H/1 * * * 1-5')])
        ])
        
        def GRADLE_HOME = tool name: 'gradle-4.10.2', type: 'hudson.plugins.gradle.GradleInstallation'
        sh "${GRADLE_HOME}/bin/gradle tasks"

        stage('Clone') {
            git url: 'https://github.com/FSTSettat/devops-webapp1.git'                
        }

        stage('Build') {
            sh "${GRADLE_HOME}/bin/gradle build -PwarName=${RELEASENAME} --info"
        }

        stage('Archive') {
            archiveArtifacts "build/libs/${RELEASENAME}*.war"
        }    
    }
//END-OF-SCRIPT
