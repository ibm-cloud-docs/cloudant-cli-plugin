#!groovy

pipeline {
    agent {
        kubernetes {
            yaml kubePodTemplate(name: 'thin.yaml')
        }
    }
    stages {
        stage("Publish") {
            environment {
                GH_CREDS = credentials('ibm-ghe')
            }
            when {
                beforeAgent true
                anyOf {
                    buildingTag()
                    branch 'review'
                }
            }
            stages {
                stage("Prepare credentials") {
                    steps {
                        sh '''
                            git config user.email $GH_SDKS_AUTOMATION_MAIL
                            git config user.name $GH_CREDS_USR
                            git config credential.username $GH_CREDS_USR
                            git config credential.helper '!f() { echo password=\$GH_CREDS_PSW; echo; }; f'
                        '''
                    }
                }
                stage("Push review to the draft branch") {
                    when {
                        branch 'review'
                    }
                    steps {
                        // Overwrite the draft branch with the latest content of review
                        sh 'git push origin HEAD:draft --force'
                    }
                }
                stage("Push review to the publish branch") {
                    when {
                        buildingTag()
                    }
                    steps {
                        // Push tagged review changes to the publish branch
                        sh 'git push origin HEAD:publish'
                    }
                }
            }
        }
    }
}
