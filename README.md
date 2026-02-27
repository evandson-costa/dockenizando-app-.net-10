Hello Docker - .NET 10 🚀

Este projeto é uma demonstração de dockenização de uma aplicação ASP.NET Core 10, focada em boas práticas de deploy e exposição de portas em ambientes Linux.
🛠 Tecnologias Utilizadas

    Plataforma: .NET 10

    Linguagem: C#

    Container: Docker

    Arquitetura: REST API

📋 Pré-requisitos

    .NET 10 SDK

    Docker Desktop ou Docker Engine no Linux.

🚀 Como Executar o Projeto
1. Publicação do Artefato

Primeiro, geramos os binários da aplicação otimizados para produção:
Bash

dotnet publish HelloDocker/HelloDocker.csproj -c Release -o ./publish

2. Construção da Imagem Docker

Com os arquivos publicados, criamos a imagem gerenciada pelo Docker:
Bash

docker build -t hello-docker:0.0.1-SNAPSHOT .

3. Execução do Container

Para rodar a aplicação mapeando a porta local 80 para a porta interna 5000 do container:
Bash

docker run -d -p 80:5000 --name hello-docker-container hello-docker:0.0.1-SNAPSHOT

🌐 Acesso

Após a execução, a API estará disponível em:

    Endpoint: http://localhost/hello-docker

🛡️ Notas de Desenvolvimento

    Portas Privilegiadas: No Linux, portas abaixo de 1024 exigem permissão de root. Por isso, a aplicação interna foi configurada para a porta 5000 e mapeada via Docker para a porta 80 (HTTP padrão).

    Versionamento: Seguindo o padrão de desenvolvimento, a imagem utiliza a tag 0.0.1-SNAPSHOT.