pipeline 
{
    agent any
    stages 
    {
        stage ( 'Build Docker Image')
        {
            steps
            {
                script
                {
                    dockerapp = docker.build("harrisonlima/pedelogo-catalogo:${env.BUILD_ID}", '-f ./src/Dockerfile ./src')
                }
            }
        }

        stage ('Push Docker Image')
        {
            steps
            {
                script
                {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub')
                    {
                        dockerapp.push('latest')
                        dockerapp.push("${env.BUILD_ID}")
                    }
                }
            }
        }

        stage ('Deploy Kubernetes')
        {
            environment
            {
                tag_version = "${env.BUILD_ID}"
            }
            steps
            {
                withKubeConfig([credentialsId: 'kubeconfig'])
                {
                    sh 'sed -i "s/{{TAG}}/$tag_version/g" ./src/k8s/api/deployment.yaml'
                    sh 'kubectl apply -f ./src/k8s -R'
                }
            }
        }
    }
}