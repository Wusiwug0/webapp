#!groovy

node('node') {


    currentBuild.result = "SUCCESS"

    try {


       stage 'Test'

            env.NODE_ENV = "test"

            print "Environment will be : ${env.NODE_ENV}"

            sh 'node -v'


       stage 'Deploy'

            cd /var/adm/webapp
            pm2 stop index.js
            git pull
            pm2 start index.js


       stage 'Cleanup'


        }

   catch (err) {

        currentBuild.result = "FAILURE"

            mail body: "project build error: ${err}" ,
            from: 'xxxx@yyyy.com',
            replyTo: 'yyyy@yyyy.com',
            subject: 'project build failed',
            to: 'zzzz@yyyyy.com'

        throw err }
}
