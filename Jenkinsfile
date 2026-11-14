@Library('Shared')_
pipeline{
    agent { label 'Agent'}
    
    stages{
        stage("Code clone"){
            steps{
                sh "whoami"
            clone("https://github.com/Vipul-Wani/django-notes-app.git","main")
            }
        }
        stage("Code Build"){
            steps{
            dockerbuild("notes-app","latest")
            }
        }
        stage("Push to DockerHub"){
            steps{
                dockerpush("dockerHubCred","notes-app","latest")
            }
        }
        stage("Deploy"){
            steps{
                 echo "This is a Deploy Code Structure"
                 sh "docker compose down &&  docker compose up -d"
            }
        }
        
    }
}
