# Built In Docker (Snippet project)

## Motivação
Ter uma implementação com a praticidade do CLI do .NET + Conteinerização

## Como funciona
Apenas com a linha de comando do dotnet é possível criar um container com a imagem da aplicação.

### Código
É preciso adicionar o pacote `Microsoft.NET.Build.Containers`

```bash
  dotnet add package Microsoft.NET.Build.Containers
```

Depois coloque as informações necessárias no .csproj, como: nome da imagem, tag e etc.

```xml
    <ContainerImageName>snippet-built-in-docker</ContainerImageName>
    <ContainerImageTags>latest</ContainerImageTags>
    <PublishProfile>DefaultContainer</PublishProfile>
    <RuntimeIdentifier>linux-x64</RuntimeIdentifier>
```

<hr>

### Instalação

1. Clone o projeto

```bash
git clone https://github.com/SauloAlmeida/snippet-built-in-docker
```

2. Acesse o diretório
```bash
cd SP.BuiltInDocker
```

3. Restaure os pacotes
```bash
dotnet restore
```

## Rodar o projeto

1. Crie uma imagem do container
```bash
dotnet publish -c Release --self-contained 
```

2. Aguarde a confirmação da criação
```bash
Pushed container 'snippet-built-in-docker:latest' to local daemon
```

3. Execute a imagem
```bash
docker run -it --rm -p 5050:80 snippet-built-in-docker:latest
```
