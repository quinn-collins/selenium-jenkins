node {
    stage ('Setup') {
        echo 'setup start'
        checkout scm
        echo 'setup complete'
    }
    stage('Run Tests') {
        echo 'starting tests'
        def rubyContainer = docker.image('dtr-test.nwie.net/ets/ruby24')
        rubyContainer.inside('-u root'){
            sh 'bundle install'
            sh "rake tests:$rake_task[$build_env]"
        }
        echo "Tests run"
    }
}
