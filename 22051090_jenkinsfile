pipeline {
    agent any
    stages {
       stage('Stage 1') {
          steps {
              echo '22051090STG1: Push change to production web server?'
              input 'Proceed or Abort?'
          }
        }
        stage('Stage 2') {
          steps {
              sh  ""#!/bin/bash
               puppet resource package git ensure=present
               puppet resource package apache2 ensure=present
               puppet resource service apache2 ensure=running
               puppet resource file /tmp/22051090/clone ensure=absent
               puppet resource file /tmp/22051090/clone ensure=directory
               git clone https://github.com/mhilmeeali/22051090_repo.git /tmp/22051090/clone
               cp /tmp/22051090/clone/index.html /var/www/html/index.html""
              input '22051090STG2 - Push to production web server completed''
          }
        } 
         stage('Stage 3') {
          steps {
              echo '22051090STG3: Proceed to test production web service?'
              input 'Proceed or Abort?'
          }
        }
         stage('Stage 4') {
          steps {
              sh 'curl -Is http://22051090-websvr.localdomain | head -n 1 > /tmp/web-test-result'
              echo 'STG4: Production web server testing completed'
          }
        }
         stage('Stage 5') {
          steps {
              echo '22051090STG5: Web server testing result has been inspected'
              input 'Proceed or Abort?'
          }
        }
         stage('Stage 6') {
          steps {
              echo '22051090STG6: Production Operation is successful.'
          }
        }
    }
 } 
