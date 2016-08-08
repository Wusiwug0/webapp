#!groovy


node('master') {


    currentBuild.result = "SUCCESS"

    try {

       stage 'Checkout'

            echo 'checkout'

       stage 'Test'

            echo 'test'
            sh 'node -v' 

       stage 'Deploy'

            echo 'Push to webservero'
            sh returnStatus: true, script: 'pm2 stop index.js’ 
            sh 'cd /var/adm/webapp; git pull'
            sh returnStatus: true, script: 'pm2 start index.js’ 

       stage 'Cleanup'

            echo 'prune and cleanup'

        }


    catch (err) {

        currentBuild.result = "FAILURE"


        throw err
    }

}
