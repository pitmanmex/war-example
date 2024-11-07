pipeline {
	agent any
	tools {
		maven 'maven 3.9.9'
	}

	parameters {
		choice(name: 'DEPLOY_ENVIRONMENT', choices: ['tomcat1', 'tomcat2'], description: 'Ambiente de despliegue')
	}

	stages {
		stage('PackageDocker') {
			steps {
				bat 'mvn -B -q -P docker-build clean package'
			}
		}
		
		stage('Deploy') {
			steps {
				bat 'D:\devenv\ambientes\tomcat1\bin\shutdown.bat'
				bat 'copy target\ROOT.war D:\devenv\ambientes\tomcat1\webapps'
				bat 'D:\devenv\ambientes\tomcat1\bin\startup.bat'
			}
		}
  
	}
}
