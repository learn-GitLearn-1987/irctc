pipeline {
  agent any

  environment {
      PATH= "/opt/maven/bin:$PATH"
    // Customize these for your repo and Maven settings
    GIT_REPO = 'https://github.com/learn-GitLearn-1987/irctc.git'
    BRANCH = 'main'
  }

  stages {

    stage('Clone Repository') {
      steps {
        echo "Cloning ${GIT_REPO}..."
        git branch: "${BRANCH}", url: "${GIT_REPO}"
      }
    }

    stage('Build WAR with Maven') {
      steps {
        echo 'Building the application using Maven...'
        sh 'mvn clean package'
      }
    }

    stage('Archive WAR') {
      steps {
        echo 'Archiving WAR file...'
        archiveArtifacts artifacts: '**/target/*.war', allowEmptyArchive: false
      }
    }
  }
}

