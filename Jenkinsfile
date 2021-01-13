pipeline{
    agent any
    
    stages{
        stage("Checkout"){
            steps{
                echo "Checking out code from Github..."
                git branch: 'main', url: 'https://github.com/rathoremayank/sample-maven-jacoco-testing.git'
            }
        }
        stage("SonarQube"){
            steps{
                echo "Starting SonarQube Analysis..."
                //mvn sonar:sonar -Dsonar.projectKey=palindrome-project -Dsonar.host.url='http://35.237.27.26:9000' -Dsonar.login=916dc468a55a59fffd4385984470869000b91268
            }
        }
        stage("Tools Initialization"){
            tools{
                maven 'jenkins-maven'
                jdk 'master-openjdk11'
            }
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                ''' 
            }
        }
        stage("Jacoco Test"){
            steps{
                echo "Testing the maven project..."
                sh 'mvn test'
            }
        }
    }
}
