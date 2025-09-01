pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        echo 'Building...'
        // build steps here (mvn/gradle/npm/etc.)
      }
    }

    stage('Test') {
      steps {
        echo 'Testing...'
        snykSecurity(
          snykInstallation: 'Snyk_Pilot_Test',          // must match Manage Jenkins → Tools → Snyk installations
          snykTokenId: 'akashsnyksecret',             // ID of your “Snyk API Token” credential
          severity: 'high',                      // low | medium | high | critical
          failOnIssues: false,                    // fail build if issues at/above severity are found
          monitorProjectOnBuild: true,           // send snapshot to Snyk for continuous monitoring
          // Optional tweaks:
          // organisation: 'your-org-slug',
          // projectName: 'my-project-name',
          // targetFile: 'pom.xml',               // or package.json, build.gradle, etc.
          // additionalArguments: '--all-projects' // or pass build-tool args after `--`
        )
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying...'
      }
    }
  }
}
