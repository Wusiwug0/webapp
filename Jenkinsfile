#!groovy


node('master') {


    currentBuild.result = "SUCCESS"

    try {

       stage 'Checkout'

            echo 'checkout'

       stage 'Test'

            echo 'test'
            sh 'node -v' 
            sh returnStdout: true, script: 'curl -I 54.149.59.2:8080'

       stage 'Deploy'

            echo 'Push to webservero'
            dir('/var/adm/webapp') {
            sh 'git pull'
            } 
            sh 'pm2 restart all'  
            sleep 10
            sh returnStatus: true, script: 'curl -I 54.149.59.2:8080'

       stage 'Cleanup'

            echo 'prune and cleanup'

        }


    catch (err) {

        currentBuild.result = "FAILURE"


        throw err
    }

}
