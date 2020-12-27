pipeline {
  agent any
  stages {
    stage('checkout') {
    	checkout([$class: 'SubversionSCM',
    	  additionalCredentials: [],
    	  excludedCommitMessages: '',
    	  excludedRegions: '',
    	  excludedRevprop: '',
    	  excludedUsers: '',
    	  filterChangelog: false,
    	  ignoreDirPropChanges: false,
    	  includedRegions: '',
    	  locations: [
    	    [cancelProcessOnExternalsFail: true,
    	      credentialsId: '7c5ee955-d4f8-4f6a-b0df-1e01ac8b3a8d',
    	      depthOption: 'infinity',
    	      ignoreExternalsOption: false,
    	      local: '.',
    	      remote: 'http://172.17.0.3/svn/basico'],
    	    [cancelProcessOnExternalsFail: true,
    	      credentialsId: '7c5ee955-d4f8-4f6a-b0df-1e01ac8b3a8d',
    	      depthOption: 'infinity',
    	      ignoreExternalsOption: false,
    	      local: '.',
    	      remote: 'http://172.17.0.3/svn/EITLookAndFeel'],
    	    [cancelProcessOnExternalsFail: true,
    	      credentialsId: '7c5ee955-d4f8-4f6a-b0df-1e01ac8b3a8d',
    	      depthOption: 'infinity',
    	      ignoreExternalsOption: false,
    	      local: '.',
    	      remote: 'http://172.17.0.3/svn/EITJava']],
    	  quietOperation: true,
    	  workspaceUpdater: [$class: 'UpdateUpdater']])
    }

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
