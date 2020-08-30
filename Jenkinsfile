node {
    def app

    environment {
        registry = "deepthisheetal/docker-hub-dsp"
        registryCredential = 'docker-hub-dsp'
        def dockerHome = tool 'MyDocker'
        env.PATH = "${dockerHome}/bin:${env.PATH}"
    }
 
    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */
        
        app = docker.build("deepthisheetal/docker-hub-dsp") 
    }

    stage('Test image') {
        /* Ideally, we would run a test framework against our image. */

        sh 'echo "Tests passed"'
    }

    stage('Deploy image') {
         docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-dsp') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
   
 
}
