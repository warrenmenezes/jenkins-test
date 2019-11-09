RELEASE_APP_NAME = 'Android-RC'
FEATURE_APP_NAME = 'Android-RC'
STAGING_APP_NAME = 'Android-RC'


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
        return RELEASE_APP_NAME
    }
    if (branch == 'dev-feature') {
        return FEATURE_APP_NAME
    }
    return STAGING_APP_NAME
}

