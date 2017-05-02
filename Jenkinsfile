node("docker") {
    docker.withRegistry('https://hub.docker.com/r/roscioa/test/', 'normal') {
    
        git url: "<<your-git-repo-url>>", credentialsId: 'normal'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "test"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
