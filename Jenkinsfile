#!/usr/bin/env groovy

def jobBuildUrl = env.BUILD_URL
def currentBranch = "*/develop"
def targetBranch = "develop"
def isRun = targetBranch == "develop" // indicate which branch to run this job
//def isRun = true // indicate which branch to run this job


node {
    def log
    try {
        stage('Task Info') {
            log = "[STAGE1]: Jenkins Task is active..."
            echo '\u2600 Runtime Environment: '
            echo "TASK: BUILD_URL=${jobBuildUrl} \n Form: ${currentBranch} \u2192 ${targetBranch}"
            sh "env"
        }
    } catch (exc) {
        echo 'ERROR: ' + exc
        throw exc
    } finally {

    }
}