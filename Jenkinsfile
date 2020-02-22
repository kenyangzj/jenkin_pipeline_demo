#!/usr/bin/env groovy

def gitSource = 'https://git.sami.int.thomsonreuters.com/data-sourcing/coconut.git'
def gitCredentialsId = 'd8615103-ece2-4e76-ae72-ea588b4e1cbc'

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
        }

        stage('Checkout Code') {
            log = "[STAGE2]: Checkout code from gitlab repo now..."
            echo 'Pull code from the gitlab server.'
            // sh "rm -rf *"
            // pull code from the gitlab server
            checkout([
                    $class                           : 'GitSCM',
                    branches                         : [[name: '*/master']]
            ])


        }

        stage('Build & UnitTest') {
            log = "[STAGE3]: Build code and run unit test with maven..."
            echo "\u2600 Build project based on given module"
            echo "mvn -B clean package"
            bat "mvn -B clean package"
//            echo "module: ${module2Deploy.toString()}"
//            if (module2Deploy != null) {
//                switch (module2Deploy) {
//                    case SubModules.ALL:
//                        //    echo "mvn -B -Dmaven.test.failure.ignore clean install"
//                        //   sh "mvn -B -Dmaven.test.failure.ignore clean install"
//                        echo "mvn -B -Dmaven.test.failure.ignore clean package shade:shade"
//                        sh "mvn -B -Dmaven.test.failure.ignore clean package shade:shade"
//                        break
//                    default:
//                        sh "mvn -B -Dmaven.test.failure.ignore clean install -pl ${module2Deploy.toString()} -am"
//                }
//            } else {
//                throw new RuntimeException("Please ensure you have specified a module...")
//            }
        }
    } catch (exc) {
        echo 'ERROR: ' + exc
        throw exc
    } finally {

    }
}