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
            dir('/var/adm/webapp') {
            // some block
            } 
            sh 'git pull'
            sh 'pm2 restart all'  

       stage 'Cleanup'

            echo 'prune and cleanup'

        }


    catch (err) {

        currentBuild.result = "FAILURE"


        throw err
    }

}
