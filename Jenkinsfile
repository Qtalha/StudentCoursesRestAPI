pipeline {
    agent(label "openjdk")
    environment{
        dockerhub=credentials('dockerhub')
    }
       stages{
        stage('pull from vcs'){
            steps {
                git url : 'https://github.com/Qtalha/StudentCoursesRestAPI.git'
                branch : 'master'
            }
            stage('build image'){
                step {
                    sh 'docker image build -t studentcoursesrestapis:1.0 .'

                }
            }
            stage ('login docker'){
                steps{ 
                    sh 'docker tag studentcoursesrestapis:1.0 quazitalha/studentcoursesrestapis:1.0'
                    sh 'echo $dockerhub_PSW | docker login -u $dockerhub_USR --password-stdin'
                    sh 'docker push quazitalha/studentcoursesrestapis:1.0'
                    sh ' docker container run -d -P studentcoursesrestapis:1.0'

                }
            }
             
            }
        }
       }
    
