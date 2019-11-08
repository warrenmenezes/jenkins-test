pipeline {
    agent any
    options {
        timestamps()
    }
    environment {
    }
    stages {
        stage('Prepare') {
            steps {
                echo 'Preparing '
                echo 'Branch Name: ${env.BRANCH_NAME}'
                getAppCenterAppNameFromBranch(branch)
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

