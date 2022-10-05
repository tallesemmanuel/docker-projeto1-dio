## Projeto servidor web utilizando o docker e docker compose.

### Requisitos

* Docker engine: Veja [https://docs.docker.com/engine/installation](https://docs.docker.com/engine/installation)

* Docker compose: Veja [docs.docker.com/compose/install](https://docs.docker.com/compose/install/)

## Iniciando instalação

Para utilizar esse projeto, faça o download do repositório.

```sh
git clone https://github.com/tallesemmanuel/docker-projeto1-dio.git
```

Entre dentro do diretório "docker-projeto1-dio".

```sh
cd docker-projeto1-dio
```

Para executar o docker compose, digite:

```sh
docker compose up -d
```

Saída do comando:

```sh
[+] Running 6/6
 ⠿ apache Pulled                                                                                                                                                                              18.1s
   ⠿ bd159e379b3b Pull complete                                                                                                                                                                7.2s
   ⠿ 36d838c2f6d6 Pull complete                                                                                                                                                                7.2s
   ⠿ b55eda22bb18 Pull complete                                                                                                                                                                7.3s
   ⠿ f6e6bfa28393 Pull complete                                                                                                                                                               10.7s
   ⠿ a1b49b7ecb8a Pull complete                                                                                                                                                               10.8s
[+] Running 2/2
 ⠿ Network docker-projeto1-dio_default  Created                                                                                                                                                0.1s
 ⠿ Container apache2-app                Started                                                                                                                                                2.5s
```

Entendendo:

Quando o comando foi executado, ele verificou se a imagem "apache" já existia localmente, como não existia, ele fez o download da imagem. Após isso, ele criou uma network utilizada e iniciou a aplicação.

Veja se o container está em execução.

```sh
docker container ls
```

Saída do comando:

```sh
CONTAINER ID   IMAGE          COMMAND              CREATED         STATUS         PORTS                               NAMES
2fe1789db158   httpd:latest   "httpd-foreground"   3 minutes ago   Up 3 minutes   0.0.0.0:80->80/tcp, :::80->80/tcp   apache2-app
```

Analisando o log do compose.

```sh
docker compose log -f
```

Saída do comando:

```sh
apache2-app  | AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.18.0.2. Set the 'ServerName' directive globally to suppress this message
apache2-app  | AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.18.0.2. Set the 'ServerName' directive globally to suppress this message
apache2-app  | [Wed Oct 05 10:57:20.725897 2022] [mpm_event:notice] [pid 1:tid 140541628747072] AH00489: Apache/2.4.54 (Unix) configured -- resuming normal operations
apache2-app  | [Wed Oct 05 10:57:20.726064 2022] [core:notice] [pid 1:tid 140541628747072] AH00094: Command line: 'httpd -D FOREGROUND'
```

Para testar, você pode ir no seu navegador e digitar "http://localhost/index.html" ou se tiver o comando curl, digitar no seu terminal "curl http://localhost/index.html".

Testando no seu navegador.

![](/arquivos_readme/png_teste_apache.png)

Testando no seu terminal.

```sh
curl http://localhost/index.html
```

Saída do comando:

```sh
➜  docker-projeto1-dio git:(main) ✗ curl http://localhost/index.html
<html>
    <h1>
        Projeto Dockerfile Bootcamp!!!
    </h1>
</html>
```

Parabéns, você conseguiu!!!

Para parar a execução do docker compose, digite:

```sh
docker compose down -v
```


## Para contribuir com esse projetoex

1. Faça todo passo acima. 
2. Commit suas mudanças (`git commit -am 'Add some fooBar'`)
3. Push sua branch (`git push origin feature/fooBar`)
4. Crie uma nova Pull Request.
