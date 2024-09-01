pipeline {
    agent any
    stages {
        stage("Install apache") {
            steps {
                echo "installing Apache"
                sh '/var/lib/jenkins/systemScripts/install_apapche2.sh'
            }
        }
        stage("checking errors") {
            steps {
                echo "Checking for errors"
                sh "ls -al /var/lib/jenkins/systemScripts/"
                sh '/var/lib/jenkins/systemScripts/test_requests.sh'
                sh 'grep -E "HTTP/1\\.[01]\\" [45][0-9]{2}" /var/log/apache2/access.log'
            }
        }
        stage("comlete work and uninstall apache2") {
            steps {
                sh "/var/lib/jenkins/systemScripts/remove_apapche2.sh" 
                echo "Work done"
            }
        }
    }
}
