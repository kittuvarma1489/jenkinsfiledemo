pipeline{
    tools{
        maven 'mymaven'
    }
    agent {label 'mavenagent'}
    parameters{
        string(name: 'gitrepo', defaultValue: 'https://github.com/kittuvarma1489/DevOpsCodeDemo.git', description: 'enter the url')
    }
    stages{
        stage('clonerepo')
        {
            steps{
                git "${params.gitrepo}"
            }
        }
        stage('compile')
        {
            steps{
                sh 'mvn compile'
            }
        }
        stage('codereview')
        {
            steps{
                sh 'mvn pmd:pmd'
            }
        }
        stage('unittest')
        {
            steps{
                sh 'mvn test'
            }
            post{
                success{
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('package')
        {
            steps{
                sh 'mvn package'
            }
        }
    }
}
