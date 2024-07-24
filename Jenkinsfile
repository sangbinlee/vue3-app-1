pipeline {
    agent any

    environment {
        // NODE_ENV = 'development'
        // NODE_ENV = 'production'
        BUILD_ID = 'dontKillMe' // Jenkins의 ProcessTreeKiller 방지
        // JENKINS_NODE_COOKIE = 'dontKillMe' // Jenkins의 ProcessTreeKiller 방지
        // PM2_HOME = '/var/lib/jenkins/.pm2'
    }
    stages {
        stage('Clone Sources') {
          steps {
            echo 'next building the application...'
            echo 'by https://jenkins.sodi9.store/github-webhook/'
            // git 'https://gitlab.com/chiminyau/ci-test.git'
          }
        }
        stage('Information') {
          steps {
            echo 'next Information...'
            sh 'node -v'
            sh 'npm -v'
          }
        }
        stage('Config') {
          steps {
            echo 'next Config...  now....'
            // sh 'npm set registry https://registry.npm.taobao.org'
            // sh 'npm set disturl https://npm.taobao.org/dist'
            // sh 'npm set chromedriver_cdnurl http://cdn.npm.taobao.org/dist/chromedriver'
            // sh 'npm set operadriver_cdnurl http://cdn.npm.taobao.org/dist/operadriver'
            // sh 'npm set phantomjs_cdnurl http://cdn.npm.taobao.org/dist/phantomjs'
            // sh 'npm set fse_binary_host_mirror https://npm.taobao.org/mirrors/fsevents'
            // sh 'npm set sass_binary_site http://cdn.npm.taobao.org/dist/node-sass'
            // sh 'npm set electron_mirror http://cdn.npm.taobao.org/dist/electron/'
          }
        }
        stage('Dependencies') {
          steps {
            sh 'npm install'
          }
        }
        // stage('Unit Test') {
        //   steps {
        //     sh 'npm run unit'
        //   }
        // }
        // stage('dev') {
        //   steps {
        //     echo 'next dev the application...  now....'
        //     echo 'next build 시 에러나서 임시로 개발로 배포  now....'
        //     // sh 'npm run dev'
        //     sh 'pm2 restart "next" || pm2 start "npm run dev" --name next'
        //   }
        // }
        stage('Build') {
          steps {
            echo 'next building the application...  now....'
            sh 'npm run build'
          }
        }
        stage('deploy') {
          steps {
            echo 'next deploying the application...  dir /var/www/vue3'
            sh 'cp dist/* /var/www/vue3'
          }
        }
        // stage('run') {
        //   steps {
        //     echo 'next building the application...  now....'
        //     // sh 'npm run dev'
        //     sh 'pm2 restart "next" || pm2 start "npm run start" --name next'
        //   }
        // } 
        // stage('test') {
        //     steps {
        //         echo 'next testing the application...'
        //     }
        // }
        // stage('run') {
        //     steps {
        //         echo 'next run the application... by node 명령  important https://jenkins.sodi9.store/github-webhook/'
        //         echo 'next run the application... by 백그라운드 로 실행해야함'
        //         echo 'next run the application... by node .output/server/index.mjs'
        //         // sh 'node .output/server/index.mjs'
        //         // sh 'export BUILD_ID=dontKillMe'
        //         // sh 'pm2 start .output/server/index.mjs -i max --name "next" -f'// 앱이 이전 꺼도 보임 refresh할때마다 다름
        //         sh ' pm2 restart "next" || pm2 start .output/server/index.mjs -i max --name "next"'
        //         sh 'pm2 save'
        //     }
        // }
    }
}
