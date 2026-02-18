# Day 81: Jenkins Multistage Pipeline

# 1. Login into the jenkins with the given credentials.

# 2. Update old plugins and install new plugins as mentioned then restart jenkins

SSH, SSH Credentials, Pipeline, Pipeline Stage view

# 3. Login again into storage server, update index file content and push changes to master branch as mentioned in the task

$ cd /var/www/html

$ vi index.html

#Update file content & push to git

$ git add .
$ git commit -m "commit message"
$ git push -u origin master

# 4. Go to Jenkins and create pipeline job

Dashboard > new items > job-name > select 'pipeline' > OK

#Script

pipeline {
    agent any

    environment {
        GIT_REPO = 'http://git.stratos.xfusioncorp.com/sarah/web.git'
        REMOTE_HOST = 'ststor01.stratos.xfusioncorp.com'
        REMOTE_PATH = '/var/www/html'
    }

    stages {
        stage('Deploy') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: 'ststor01', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                        sh """
                        sshpass -p "$PASS" ssh -o StrictHostKeyChecking=no $USER@$REMOTE_HOST "cd $REMOTE_PATH && git pull"
                        """
                    }
                }
            }
        }
        stage('Test') {
            steps {
                sh 'curl -f http://stlb01:8091'
            }
        }
    }
}


#Then Apply and Save!!

# 5. Build the job and click on APP button to access the application!!

If there is any issues, check console output of build and fix that.
