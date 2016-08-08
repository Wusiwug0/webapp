#!groovy


node('node') {


    currentBuild.result = "SUCCESS"

    try {

       stage 'Checkout'

            echo 'checkout'm

       stage 'Test'

            echo 'test'
            sh 'node -v'


       stage 'Deploy'

            echo 'Push to webservero'

       stage 'Cleanup'

            echo 'prune and cleanup'

        }


    catch (err) {

        currentBuild.result = "FAILURE"


        throw err
    }

}
