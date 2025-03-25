pipeline {
    agent any
    environment {
        AZURE_CREDENTIALS = credentials('AzureServicePrincipal')
        AZURE_RESOURCE_GROUP = 'jenkins-get-started-rg'
        AZURE_WEBAPP_NAME = 'myjenkinsapp-yizhe928'
        PATH = "/opt/homebrew/bin:$PATH"
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Azure') {
            steps {
                sh '''
                    az login --service-principal -u $AZURE_CREDENTIALS_USR -p $AZURE_CREDENTIALS_PSW --tenant 59ad9ca7-0d3c-41d4-a2b2-c259b4dd2029
                    az webapp deploy --resource-group $AZURE_RESOURCE_GROUP --name $AZURE_WEBAPP_NAME --type war --src-path target/*.war
                '''
            }
        }
    }
}


