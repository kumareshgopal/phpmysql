node{

    stage('SCM Checkout')
    {
        git credentialsId: '16ed4794-8298-4a3e-8e2c-748307eadd0a', url: 'https://github.com/kumareshgopal/phpmysql.git'
    }
    
    stage('Run Docker Compose File')
    {
        sh 'docker-compose build'
        sh 'docker-compose up -d'
    }
    stage('PUSH image to Docker Hub')
    {
        withCredentials([string(credentialsId: 'DockerHubPassword', variable: 'DHPWD')]) 
        {
            sh "docker login -u 12081984 -p ${DHPWD}"
        }
        sh 'docker push 12081984/phpmysql'
    }
}
