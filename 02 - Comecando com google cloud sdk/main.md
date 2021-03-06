# Conhecendo o SDK

### Instalando


### MacOS

Vamos utilizar o brew:

```
brew tap caskroom/cask
brew cask install google-cloud-sdk
```

Para validar se o gcloud foi instalado com sucesso execute o seguinte comando:

```
gcloud --version
```

Ele deve te retornar algo como:

![gcloud --version](./img/gcloud-version.png)


## Windows 

Certifique-se que o Python está instalado na sua máquina corretamente.

Faça o download do [Instalador do Google Cloud SDK](https://dl.google.com/dl/cloudsdk/channels/rapid/GoogleCloudSDKInstaller.exe).

Inicie o instalador e siga as instruções.

Depois que a instalação for concluída, o instalador apresenta várias opções:

![gcloud windows-install](./img/windows-installer-prompt.png)

Verifique se as opções abaixo estão selecionadas:

 * Start Google Cloud SDK Shell (Iniciar Shell do Google Cloud SDK)
 * Run 'gcloud init' (Executar 'gcloud init')
 * O instalador abre uma janela de terminal e executa o comando gcloud init.

Dica de solução de problemas: caso sua instalação não tenha sucesso devido a uma falha de reconhecimento do comando find, verifique se a variável de ambiente PATH está configurada para incluir a pasta que contém find. Normalmente, é a `C:\WINDOWS\system32`;.


## Linux

Antes de começar
Verifique se o sistema operacional é um dos seguintes itens:

 * uma versão do Ubuntu que não atingiu o fim da vida útil
 * uma versão estável do Debian a partir da Wheezy
 
 Em seguida, realize as seguintes etapas:

* Criar variável de ambiente para distribuição correta
```
export CLOUD_SDK_REPO="cloud-sdk-$(lsb_release -c -s)"
```

* Adicione o URI de distribuição do Cloud SDK como uma fonte de pacote
```
echo "deb http://packages.cloud.google.com/apt $CLOUD_SDK_REPO main" | sudo tee -a /etc/apt/sources.list.d/google-cloud-sdk.list
```
* Importar a chave pública do Google Cloud Platform
```
curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
```

* Atualize a lista de pacotes e instale o Cloud SDK
```
sudo apt-get update && sudo apt-get install google-cloud-sdk
```

###


### Configurando o gcloud

Comece executando o comando 

```
gcloud init
```

e siga o passo a passo.

* De um nome para a configuração
* Faca login com sua conta do Google
* Escolha o projeto criado ou crie um novo

E isso, agora você já tem seu projeto cadastrado e podemos começar a utilizar a cli (command line interface) para executar nossos comandos!



### Criando um projeto pela sdk

A primeira dica vai pro comando `man`, muito provavelmente você não conhece os parâmetros de nenhum comando do gcloud. Então você vai precisar bastante do `man`. 

Faca o seguinte digito o comando `man gcloud` e aperta tab. 
Você deve estar vendo uma lista gigante de comandos. Mas nos queremos ver comandos relacionados a projetos, então vamos tentar reduzir essa lista executando `man gcloud_projects` e pressionando tab novamente.
Beleza, agora temos uma lista bem menor...

Você consegue ate ler as opções, e ver que temos uma que e create. 
Seguimos com o comando `man gcloud_projects_create`.
De uma lida em como o comando funciona e todos os parâmetros.

Caso você não queira ler agora, basta digital `gcloud projects create $id_unico`, trocando $id_unico para o id do seu projeto. 

![gcloud projects create](./img/new-project.png)

Não vamos precisar desse projeto, pois já criamos o nosso anteriormente.
Então vamos aproveitar para aprender a deletar um projeto.

Supondo que a gente não saiba o id do projeto, nem quais projetos existem podemos simplesmente rodar o comando `gcloud projects list`

![gcloud projects list](./img/gcloud-projects-list.png)

Agora que sabemos os projetos existentes podemos deletar com `gcloud projects delete $id_unico`

![gcloud projects delete](./img/gcloud-projects-delete.png)

Se você ler com atenção a saída do comando vai aprender mais um novo comando:

`gcloud projects undelete $id_unico`

Por padrão a GCP não deleta instantaneamente seu projeto, ele joga o projeto em uma espécie de quarentena que dura em torno de 30 dias. Quando esse prazo vai chegando ao final, eles enviam um e-mail para você falando que seu projeto será deletado em breve.

Ate esse dia você pode desfazer o comando de delete e recuperar o projeto.

Vale a pena mencionar que você recebera um e-mail, assim que mandar deletar o projeto, avisando que foi agendado a deleção do projeto.

![email delecao do projeto](./img/delecao-do-projeto.png)


# Links uteis
- https://cloud.google.com/sdk/gcloud/reference/