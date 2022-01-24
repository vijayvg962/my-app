pipeline{
    agent any
    triggers{
        pollSCM '* * * * *'
    }
    stages{
        stage("maven"){
            when{
                branch "develop"
            }
            steps{
                sh "mvn package"
            }
        }
        stage("maven build"){
            when{
                branch "qa"
            }
            steps{
                sh "mvn package"
            }
        }
        stage("sonarQube"){
            when{
                branch "qa"
            }
            steps{
                echo "sonarqube analysis..."
            }
        }
        stage("nexus"){
            when{
                branch "develop"
            }
            steps{
                echo "deploying to qa server...."
            }
        }
        stage("Deploy To QA"){
            when{
                branch "master"
            }
            steps{
                echo "deploying to qa server...."
            }
        }
        stage("Deploy To production"){
            when{
                branch "master"
            }
            steps{
                echo "deploying to master server..."
            }
        }
    }
}
