pipeline {
	agent any
	tools {
		maven 'maven 3.9.9'
	}

	parameters {
		choice(name: 'DEPLOY_ENVIRONMENT', choices: ['ninguno', 'tomcat1', 'tomcat2'], description: 'Ambiente de despliegue')
	}

	stages {
		stage('PackageDocker') {
			steps {
				bat 'mvn -B -q -P docker-build clean package'
			}
		}
		
		stage('Deploy') {
			when {
				not {
					equals expected: 'ninguno', actual: params.DEPLOY_ENVIRONMENT
				}
			}
			steps {
				/*bat 'D:\\devenv\\ambientes\\tomcat1\\bin\\shutdown.bat'*/
				bat 'copy target\\ROOT.war D:\\devenv\\ambientes\\' + params.DEPLOY_ENVIRONMENT + '\\webapps'
				/*bat 'D:\\devenv\\ambientes\\tomcat1\\bin\\startup.bat'*/
			}
		}
  
	}
}
