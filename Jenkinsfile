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
            steps {
                echo 'Preparing '
                echo "Branch Name: ${env.BRANCH_NAME}"
                getAppCenterAppNameFromBranch(env.BRANCH_NAME)
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

