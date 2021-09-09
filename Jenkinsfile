pipeline {
    agent any
    
    tools {
        maven 'MAVEN_PATH'
        jdk 'jdk11'
    }
        
    stages {
        stage("Tools initialization") {
            steps {
                sh "mvn --version"
                sh "java -version"
            }
        }
            
        stage ('Clone') {
            steps {
                git branch: 'master', url: "https://github.com/adobe/aem-guides-wknd.git"
            }
        }
            
       stage ('Exec Maven') {
          steps {
              rtMavenRun (
                  tool: MAVEN_TOOL, // Tool name from Jenkins configuration
                  goals: 'clean install',
                  deployerId: "MAVEN_DEPLOYER",
                  resolverId: "MAVEN_RESOLVER"
              )
          }
      }
      stage("deploy") {
            steps {
                script {
                  def response = sh(script: 'curl https://localhost:4502', returnStdout: true)
                  
                }
            }
      }
    }
}