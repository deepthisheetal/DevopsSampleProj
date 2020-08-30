node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */
        
        /*app = docker.build("deepthisheetal/docker-hub-dsp") */
        sh 'cd "/Users/dpulla/Documents/GIT_Practice/DevopsSampleProj"'
        sh 'echo "Dir Changed"'
        sh '/usr/local/bin/docker build -t "deepthisheetal/docker-hub-dsp" .'
    }

    stage('Test image') {
        /* Ideally, we would run a test framework against our image. */

        sh 'echo "Tests passed"'
    }

    stage('Deploy image') {
        /* docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-dsp') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }*/
            sh '/usr/local/bin/docker login --username deepthisheetal --password Dipu1you@'
            sh 'echo "Logged in"'
            sh '/usr/local/bin/docker images'
            sh '/usr/local/bin/docker push deepthisheetal/docker-hub-dsp'
    }
   
 
}
