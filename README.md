# Pipeline_dados
Esse é um projeto desenvolvido para o curso de aprofundamento em data science

Nele recebemos dados de produtos de duas empresas que vão se juntar, nosso trabalho é analisar e juntar esses arquivos

Para começar esse projeto e neccesario seguir alguns passos:
O uso do WSL para desenvolvimento de projetos de engenharia de dados oferece a vantagem de proporcionar acesso a um ambiente Linux completo, sem a necessidade de uma máquina virtual ou dual boot. Além disso, o WSL permite a integração perfeita com o sistema operacional Windows.

Instalando o Windows Terminal
O terminal do Windows é um aplicativo que permite utilizar diferentes shells de linha de comando, como o Prompt de Comando, PowerShell e o WSL. Esse terminal nos permite abrir diferentes abas com cada um desses shells e personalizá-los.

Pode ser que você já tenha o terminal do Windows instalado, mas caso não tenha, é importante realizar a instalação pois vamos utilizá-lo no decorrer do curso para abrirmos nosso terminal do WSL. Para instalá-lo é simples: na barra de pesquisa do Windows, pesquise por "Microsoft Store":

Alt text: Captura de tela da barra de pesquisa do Windows com o texto "Microsoft Store" digitado. Acima da barra de pesquisa aparece a opção correspondente ao texto pesquisado, também chamada de "Microsoft Store". Esse aplicativo está destacado por um retângulo vermelho.

Ao abrir a loja de aplicativos da Microsoft, na barra de pesquisa, pesquise por "Windows Terminal" e selecione a opção "Windows Terminal":

Alt text: Captura da tela inicial do aplicativo Microsoft Store. Na parte superior central desse app existe uma barra de pesquisa com o texto "Windows Terminal" digitado. Abaixo dessa barra de pesquisa são apresentadas 3 opções correspondentes a pesquisa, a segunda opção está destacada por uma seta vermelha.

Feito isso, você pode selecionar e instalar essa ferramenta. Uma vez concluída a instalação, para abrir esse terminal, você pode pesquisar por "Terminal" na barra de pesquisa do Windows:

Alt text: Captura de tela da barra de pesquisa do Windows com o texto "Terminal" digitado. Acima da barra de pesquisa aparece a opção correspondente ao texto pesquisado, também chamada de "Terminal". Esse aplicativo está destacado por um retângulo vermelho.

Instalando o WSL 2 com Ubuntu 22.04
Para começar a instalação do WSL 2, você pode abrir como administrador o terminal do Windows que baixamos anteriormente:

Alt text: Captura de tela da barra de pesquisa do Windows com o texto "Terminal" digitado. Acima da barra de pesquisa aparece a opção correspondente ao texto pesquisado, também chamada de "Terminal". Esse aplicativo está destacado por um retângulo vermelho e há um balão com opções relacionadas a ele: a opção “Executar como administrador” está destacada com uma seta vermelha.

Após esse processo, ele abrirá automaticamente uma aba inicial nesse terminal com o Windows Powershell:

Alt text: Captura de tela do terminal do Windows Powershell

Caso o seu terminal não abra o Powershell por padrão, você pode clicar na setinha apontada para baixo, na barra superior do terminal, e selecionar o Powershell:

OBS: Dependendo da sua versão de windows é necessário apertar a tecla CTRL para abrir uma nova janela.

Alt text: Captura de tela do terminal do Windows Powershell. Na barra superior do terminal há uma seta para baixo destacada por um retângulo vermelho. Abaixo dessa seta, existem algumas opções e a primeira delas "Windows Powershell", está destacada por um retângulo vermelho.

Em seguida, podemos executar o comando:

wsl --list --online
Copiar código
Esse comando vai listar algumas versões do Ubuntu disponíveis para instalarmos.

Alt text: Captura de tela do terminal do Windows Powershell em que o comando "wsl –list –online" foi executado. Como resultado, foram disponibilizados diversos nomes de diferentes distribuições e versões Linux.

Nós vamos instalar a distribuição "Ubuntu-22.04", para isso podemos executar o comando:

wsl --install -d Ubuntu-22.04
Copiar código
Depois disso, vamos aguardar até que a instalação seja finalizada. Pode ser necessário pressionar a tecla "Enter" em alguns momentos para prosseguir com a instalação. E, após a execução desse comando, caso apareça a mensagem "As alterações só terão efeito depois que o sistema for reiniciado.", é importante que você reinicie sua máquina para prosseguir.

Caso essa mensagem não apareça, deve ser aberto um segundo terminal onde você deverá informar o nome de usuário que deseja utilizar no Linux e também sua senha.

E pronto, agora temos o WSL funcionando!

Podemos fechar os terminais abertos e, em seguida, abrir novamente o terminal do Windows. Uma vez nesse terminal, podemos clicar na seta localizada na barra superior e selecionar o "Ubuntu-22.04 LTS" para abrirmos o terminal do nosso Linux:

Alt text: Captura de tela do terminal do Windows Powershell. Na barra superior do terminal há uma seta para baixo destacada por um retângulo vermelho. Abaixo dessa seta, existem algumas opções e a quinta delas "Ubuntu-22.04 LTS" está destacada por um retângulo vermelho.

Atenção: Vale ressaltar que você precisa abrir o Terminal como administrador apenas no momento de fazer a instalação do WSL. Uma vez que isso foi realizado, você pode passar a abrir o Terminal como usuário comum.

Para o desenvolvimento de suas habilidades neste projeto, vamos iniciar com a preparação adequada do seu ambiente. Neste primeiro passo, Você pode fazer o download dos dados neste link_csv, link_json ou realizar o comando wget com as URLs.

Para desenvolver o projeto, nós vamos utilizar a linguagem Python e também vamos criar um ambiente virtual.

Instalando pacotes
Antes de realizarmos a instalação de alguns pacotes Python, é importante atualizarmos os pacotes já instalados no WSL. Para isso, podemos abrir o terminal do WSL e executar os seguintes comandos:

sudo apt-get update
Copiar código
sudo apt-get upgrade -y
Copiar código
Feito isso, confira se você tem o Python instalado. Você pode fazer isso verificando a versão dele:

python3 --version
Copiar código
ou

python3 -V
Copiar código
A versão instalada na minha máquina é a 3.10.6.

Caso não esteja nessa versão você pode rodar os comandos

sudo apt update
sudo apt install python3.10
Copiar código
Agora, você pode instalar as bibliotecas pip e venv do Python:

sudo apt install python3-pip -y
Copiar código
sudo apt install python3-venv -y
Copiar código
Criando um ambiente virtual
Um ambiente virtual Python é como uma caixa separada onde você pode instalar e gerenciar pacotes Python para um projeto específico, sem interferir em outros projetos ou no Python do sistema.

Antes de partirmos para a criação do nosso ambiente virtual, vamos criar uma pasta para o nosso projeto. Para isso, podemos abrir o terminal do WSL e utilizar o comando mkdir:

mkdir pipeline_dados
Copiar código
Acesse a pasta:

cd pipeline_dados
Copiar código
Feito isso, podemos executar o comando para criação do ambiente virtual:

python3 -m venv venv
Copiar código
Em seguida, podemos ativar o ambiente:

source venv/bin/activate
Copiar código
Com o ambiente ativado, podemos instalar as bibliotecas que vamos utilizar no decorrer do nosso projeto:

pip install requests==2.28.2
Copiar código
pip install pandas==2.0.0



