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
                APP_NAME = getAppCenterAppNameFromBranch(env.BRANCH_NAME)
            }
            steps {
                echo 'Preparing'
                sh 'git submodule update --init --recursive'
                echo "Branch Name: $APP_NAME"

            }
        }
    }
}

def getAppCenterAppNameFromBranch(String branch) {
    if (branch.startsWith('release/')) {
        return 'Android-RC'
    }
    if (branch == 'dev-feature') {
        return 'Android-Feature'
    }
    return 'Fiix-CMMS-Staging';
}

