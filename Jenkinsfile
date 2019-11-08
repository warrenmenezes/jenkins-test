pipeline {
    agent any
    options {
        timestamps()
    }
    environment {
        DEV_VERSION_FILE = "../../../dev-ci-version.properties"
    }
    stages {
        stage('Prepare') {
            environment {
                APP_NAME = getAppCenterAppNameFromBranch()
            }
            steps {
                echo 'Preparing'
                sh 'git submodule update --init --recursive'
                echo "Branch Name: $APP_NAME"

            }
        }
    }
}

def getAppCenterAppNameFromBranch() {
    if ($ { env.BRANCH_NAME }.startsWith('release/')) {
        return 'Android-RC'
    }
    if ($ { env.BRANCH_NAME } == 'dev-feature') {
        return 'Android-Feature'
    }
    return 'Fiix-CMMS-Staging';
}

