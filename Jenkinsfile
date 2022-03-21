node {

    stage('SCM Clone') {
        git credentialsID: 'github' ,url: 'https://github.com/diablll/GitOps.git'
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email ganabajo24@gmail.com"
                        sh "git config user.name diablll"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+bajod/spring.*+bajod/spring:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/Gitops.git HEAD:master"
      }
    }
  }
}
}
