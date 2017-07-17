podTemplate(label: 'python', containers: [
  containerTemplate(name: 'python', image: 'nickp666/jenkins-jnlp-docker-python:latest', ttyEnabled: true, command: 'cat')
]) {

    node('python') {
      container('python') {
        stage('Checkout from SCM') {
            checkout scm
        }

        stage('Install dependencies') {
          sh('pip install ansible ansible-lint')
        }

        stage('Set ansible roles path') {
          sh('printf "[defaults]\nroles_path=../" > ansible.cfg')
        }

        stage('Run ansible syntax check') {
          sh('ansible-playbook tests/test.yml -i tests/inventory --syntax-check')
        }

        stage('Run ansible lint') {
          sh('ansible-lint -p . > lint.report')
        }

        stage('Bitch and moan if required') {
          step([$class: 'WarningsPublisher',
            parserConfigurations: [
              [parserName: 'Pep8', pattern: 'lint.report']
            ], unstableTotalAll: '0', usePreviousBuildAsReference: true
          ])
        }
      }
    }
}
