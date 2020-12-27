pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        withGradle()
      }
    }

    stage('test') {
      steps {
        withGradle()
      }
    }

    stage('assemble') {
      steps {
        withGradle()
      }
    }

    stage('simulator') {
      parallel {
        stage('simulator') {
          steps {
            withGradle()
          }
        }

        stage('production') {
          steps {
            withGradle()
          }
        }

      }
    }

  }
}