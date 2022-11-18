### Sobre o projeto
O projeto kube-news é um projeto desenvolvido em NodeJS. O projeto tem como objetivo ser um exemplo para a criação de ambiente com containers usando NodeJS.

### Observações do projeto
A aplicação é exposta usando a porta 8080

### Observação do build
Ir para a pasta src, e então executar o docker build para geração da imagem, e então alterar na pasta k8s/deployment-web.yaml

### Observação do inicio do cluster
Executar kubectl apply -f k8s/

### Acesso dos 2 programas
Na hora de criar o cluster k3d, você tem q dar 2 port binding, como mostrado abaixo:
k3d cluster create meucluster -p "8080:30000" -p "80:31000"
Onde o localhost:8080 acessa o kube-news e o localhost acessa o pgadmin4

# Project kube-news

### About the project
The project kube-news is a project developed in NodeJS. The project goal is to be a example to environment creation with containers using NodeJS.

### Project observation
The application runs using PORT 8080

### Build Observation
Go to src folder, then execute docker build to generate the image, then changes the image name in the file deployment-web.yaml in k8s folder

### Cluster initialize Observation
Execute kubectl apply -f k8s/

### Access both programs
Before create the cluster k3d, You have to port binding both of them, as shown next:
k3d cluster create meucluster -p "8080:30000" -p "80:31000"
localhost:8080 access kube-news and localhost access pgadmin4