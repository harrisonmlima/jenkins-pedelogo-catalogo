# Projeto pedelogo-catalogo

### Sobre o projeto
O projeto pedelogo-catalogo é um projeto desenvolvido em .NET. O projeto tem como objetivo ser um exemplo para a criação de ambiente com containers usando .NET.

### Observações do projeto
A aplicação é exposta usando a porta 80

### Observação do build
Ir para a pasta src, e então executar o docker build para geração da imagem, e então alterar na pasta k8s/api/deployment.yaml

### Observação do inicio do cluster
Executar kubectl apply -f k8s/db -f k8s/api


# Project pedelogo-catalogo

### About the project
The project pedelogo-catalogo is a project developed in .NET. The project goal is to be a example to environment creation with containers using .NET.

### Project observation
The application runs using PORT 80

### Build Observation
Go to src folder, then execute docker build to generate the image, then changes the image name in the file deployment-web.yaml in k8s folder

### Access both programs
Before create the cluster k3d, You have to port binding both of them, as shown next:
k3d cluster create meucluster -p "8080:30000"
localhost/swagger access pedelogo-catalogo and localhost/mongo access mongo-express 