node {
	def app

	stage('Clone repository') {
		checkout scm
	}

	stage('Build image') {
		app = docker.build("alpapapo/example-app")
	}

	stage('Test') {
		app.inside {
			sh 'npm test'
		}
	}

	stage('Push image') {
		docker.withRegistry('https://ragnarok.earthnet.ai', 'ragnarok-credentials') {
			app.push('latest')
		}
	}

	
}
