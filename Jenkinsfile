#!groovy

node('node') {


    currentBuild.result = "SUCCESS"

    try {

       stage 'Checkout'

            checkout scm

       stage 'Test'

            env.NODE_ENV = "test"

            print "Environment will be : ${env.NODE_ENV}"

            sh 'node -v'
            sh 'npm prune'
            sh 'npm install'


       stage 'Deploy'

            echo 'Push to Repo'
            pm2 stop index.js
            git url: 'https://github.com/Wusiwug0/webapp/'		
            git pull
            pm2 start index.js


       stage 'Cleanup'

            echo 'prune and cleanup'
            sh 'npm prune'
            #sh 'rm node_modules -rf'

            mail body: 'project build successful',
                        from: 'xxxx@yyyyy.com',
                        replyTo: 'xxxx@yyyy.com',
                        subject: 'project build successful',
                        to: 'yyyyy@yyyy.com'

        }


    catch (err) {

        currentBuild.result = "FAILURE"

            mail body: "project build error: ${err}" ,
            from: 'xxxx@yyyy.com',
            replyTo: 'yyyy@yyyy.com',
            subject: 'project build failed',
            to: 'zzzz@yyyyy.com'

        throw err
    }

}
