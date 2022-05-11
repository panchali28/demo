pipeline {
  agent any
  stages {
    stage('Yocto Setup') {
      steps {
        sh '''#!/bin/bash

ADMIN_PASSWD=admin
target=admin@172.16.50.1
jfrog_auth="boole_jenkins_in:TOKEN"
machine="atlas-ii-z8ev-appmat-aurora"
yocto_dir=${HOME}/amrfpu-amrfpu-ondemand
if [ -d "$yocto_dir" ]; then 
  am-bake setup --branch amrfpu --npm-hack \\
  --jfrog-auth ${jfrog_auth} \\
  --sstate-dir /home/jenkins/yocto-cache/sstate-cache \\
  --dl-dir /home/jenkins/yocto-cache/downloads \\
  --machine ${machine} \\
  ${yocto_dir}
  retVal=$?
  if [ $retVal -ne 0 ]; then
    echo "Yocto Setup failed"
    echo "Removing $yocto_dir"
    rm -rf ${yocto_dir}

  fi
fi

echo "Yocto Setup Done"'''
      }
    }

  }
}