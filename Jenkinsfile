pipeline {
    agent any

  stages {
     stage("Initial cleanup") {
       steps {
            dir("${WORKSPACE}") {
              deleteDir()
            }
          }
        }


    stage('Checkout SCM') {
      steps {
            git branch: 'test', url: 'https://github.com/genejike/php-todo.git'
      }
    }


    stage('Prepare Dependencies') {
      steps {
             sh 'mv .env.sample .env'
             sh 'composer update'
             sh 'composer install'
             sh 'composer  self-update'
             sh 'php artisan migrate'
             sh 'php artisan db:seed'
             sh 'php artisan key:generate'
      }
    }
  }
}
