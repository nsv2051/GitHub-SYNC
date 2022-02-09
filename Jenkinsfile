pipeline {
  agent any
  stages {
    stage('检出 GitHub') {
      steps {
        checkout([
          $class: 'GitSCM',
          branches: [[name: env.GIT_BUILD_REF]], 
          userRemoteConfigs: [[url: env.GIT_REPO_URL, credentialsId: env.CREDENTIALS_ID]]
        ])
      }
    }
    stage('推送到 CODING') {
      steps {
        // 无需修改 PROJECT_TOKEN_GK 和 PROJECT_TOKEN，它们为 CODING 内置环境变量
        // 请修改为你的代码库链接
        sh "git push https://${PROJECT_TOKEN_GK}:${PROJECT_TOKEN}@e.coding.net/nsv/MRI/GitHub-SYNC.git HEAD:master"
      }
    }
  }
}
