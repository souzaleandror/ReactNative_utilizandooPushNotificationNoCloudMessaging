##### 23/01/2024

Curso de React Native: utilizando o Push Notification no Cloud Messaging


```
npx expo init gatito
npx expo start
npm install -g json server
npm install json-server@alpha
npm i
npm fund
npm audit fix
npm cache clean --force
rm -rf node_modules
npm install
npx expo start
json-server db.json
json-server --watch --host 192.168.178.24  db.json
npm start
touch db.json
npx expo install react-native-web@~0.19.6 react-dom@18.2.0 @expo/webpack-config
npm install webpack-dev-server
npm install @react-native-async-storage/async-storage
npx expo run:ios
npx expo run:android
```


@01-Entendendo Firebase Cloud Messaging

@@01
Apresentação

Olá! Eu sou André Cunha, instrutor de Mobile. Boas-vindas a mais um curso da Formação Firebase com React Native.
Autodescrição: sou um homem de pele parda, cabelo castanho escuro curto e olhos castanho escuro também. Estou usando uma camiseta azul-marinho. Ao fundo, há um parede de madeira com iluminação azul clara.
O que vamos aprender?
Neste curso, continuaremos trabalhando com o SpaceApp, um aplicativo dedicado à postagem de eventos do universo. Nós estamos o utilizando desde o curso sobre Firebase Cloud Storage.

Vamos aprender a usar o Push Notification, utilizando Firebase Cloud Messaging — mais um serviço oferecido pelo Firebase. Além da aplicação mobile que vamos desenvolver, também utilizaremos uma aplicação web para simular o envio de notificação. Ela se comunicará com uma API que construiremos ao longo do curso, para enviar notificações de forma personalizada às pessoas usuárias.

Utilizar notificações em um aplicativo é muito relevante, porque alerta a pessoa usuária sobre eventos novos até mesmo se o aplicativo não estiver aberto. Entre outras opções, é possível notificar atualizações, mensagens recebidas ou conteúdos novos que chegaram na aplicação.

Tudo isso é bom para manter o engajamento do uso da nossa aplicação. Às vezes, dependendo da frequência em que o conteúdo é atualizado, a pessoa usuária pode deixar usar a aplicação. As notificações são importíssimas para manter o uso frequente do aplicativo.

Quais os pré-requisitos?
Para acompanhar este curso, espera-se que você já tenha conhecimento do React Native com Expo e tenha assistido ao curso de Firebase Firestore.

Ficou intessado? Vamos estudar!

@@02
Orientações iniciais

Vamos continuar mergulhando no mundo do React Native e dessa vez explorando o Firebase Cloud Messaging. Você aprenderá como enviar notificações push para o seu aplicativo React Native através do serviço de mensagens do Firebase.
Neste curso, assumimos que você saiba os seguintes tópicos:

O que é o Firebase;
Como criar um projeto do Firebase e configurar um App React Native;
Como integrar o Firebase com um App React Native e adicionar as suas respectivas bibliotecas;
Criar um banco de dados no Firestore.
Esse conteúdo é apresentado no curso React Native: Firebase Authentication, e a configuração no Firestore no curso de React Native: armazenando dados no Firestore.

Se preferir, você pode seguir o tutorial da documentação. Caso você não tenha feito o curso, mas acredita que possa começar a partir daqui, fique à vontade para continuar.

Durante esta jornada, além das videoaulas, você terá atividades prática e teóricas para que possa testar seus conhecimentos, material extra para se aprofundar ainda mais nos seus estudos, como também desafios para colocar em prática seus conhecimentos.

Preparado(a)? Podemos começar.

Bons estudos!

https://cursos.alura.com.br/course/react-native-autenticacao-firebase

https://cursos.alura.com.br/course/react-native-armazenando-dados-firestore

https://firebase.google.com/docs/firestore/quickstart?hl=pt#create

@@03
Conhecendo o Firebase Cloud Messaging

Atualmente, aplicativos que postam informações são muito importantes. Mas, dependendo da frequência com que essas informações são postadas, uma pessoa pode perder interesse pelo aplicativo e abri-lo menos vezes, o que não é ideal. Queremos que as pessoas abram nosso aplicativo todo dia!
Para manter o engajamento e incentivar as pessoas a acessarem o aplicativo com mais frequência, podemos enviar notificações. Elas podem ser enviadas quando uma postagem nova for feita, para avisar sobre a possibilidade de cadastro em novos eventos ou qualquer outra informação sobre a qual a pessoa goste de ser notificada.

Por exemplo, existem aplicativos que postam informações cotidianas. Se sabemos que uma pessoa deseja receber novidades sobre esportes, podemos enviar notificações somente quando houver novas postagens sobre esse assunto em específico.

Um dos serviços oferecidos pelo Firebase chama-se Cloud Messaging, que permite o envio de mensagens para dispositivos — tanto mensagens de texto quanto notificações. As notificações podem aparecer de formas diversas na tela, incluindo apenas um título, ou um título e uma descrição, ou até mesmo uma foto!

Diferentemente dos demais, esse serviço do Firebase não tem custo, então podemos enviar quantas notificações quisermos. Existem algumas limitações, mas elas não afetarão o andamento do nosso curso. Por exemplo, só podemos enviar 500 notificações simultaneamente.

Usando o serviço do Firebase, temos confiabilidade. Vamos perceber que as mensagens não chegam instantamente, porém podemos tratá-las quando elas chegarem aos dispositivos.

Pra obter mais informações, vamos acessar a página de introdução da documentação do Firebase Cloud Messaging.

Na documentação, usa-se a sigla FCM para fazer referência ao recurso Firebase Cloud Messaging.
Dentre os principais recursos do Cloud Messaging, temos:

o envio de mensagens de notificação ou mensagens de dados, para alterar internamente as informações exibidas no aplicativo
segmentação das mensagens versátil, para distribuir mensagens para um único dispostivo ou um grupo específico de dispositivos, por exemplo, um grupo de inscritos no tópico de esportes
envio de mensagens como bate-papo, semelhante ao WhatsApp ou Instagram, que notificam a pessoa usuário quando há novas mensagens
Para utilizar esse recurso, precisamos configurar o Firebase na nossa aplicação. Ou seja, será preciso lidar um pouco com código nativo, dado que o Firebase oferece o serviço tanto para Android e iOS.

@@04
Sobre o Firebase Cloud Messaging

Aprendemos que o Firebase Cloud Messaging (FCM) é uma possível solução para o problema de falta de engajamento dos usuários, pois permite que os desenvolvedores enviem notificações push e mensagens de dados para os usuários, mantendo-os engajados e informados sobre novos conteúdos e atualizações.
Considerando o que foi estudado, marque as alternativas corretas sobre o FCM:

Permite que os desenvolvedores enviem notificações push para aplicativos em dispositivos móveis, independentemente do sistema operacional.
 
O FCM é uma plataforma de envio de notificações para dispositivos móveis que suporta a maioria dos sistemas operacionais, incluindo Android e iOS. Isso significa que os desenvolvedores podem enviar notificações push para aplicativos em dispositivos móveis, independentemente do sistema operacional utilizado, tornando mais fácil e conveniente para eles atingir seu público-alvo.
Alternativa correta
O FCM é considerado uma forma de disparar notificações push estáticas, sem o suporte a envio de mensagens de dados.
 
Alternativa correta
As notificações push enviadas com o FCM funcionam de forma global, ou seja, não permite que um usuário ou um grupo específico de usuários receba notificações personalizadas.
 
Alternativa correta
Permite o envio de notificações push para os dispositivos Android ou iOS, sendo preciso escolher qual dos sistemas receberá, impedindo o uso simultâneo para as duas plataformas.

@@05
Preparando o ambiente: instalação de software

Para realizar o curso, é preciso que você tenha alguns softwares instalados na sua máquina. Por isso, antes de continuar nossa jornada de aprendizado, é preciso que você leia com atenção algumas instruções e baixe os materiais necessários.
Instalação do Expo
Neste curso, utilizaremos um aplicativo chamado SpaceApp, que vai nos auxiliar durante toda a nossa joarnada de estudos sobre o Firebase Cloud Messaging.

Esse aplicativo foi construído no React Native com Expo, por isso, é necessário tê-lo instalado na sua máquina. Caso você não o tenha, separamos um artigo de Como instalar e configurar o Expo do React Native de forma descomplicada.

Donwload do código no Git
Após concluir a instalação, você também pode acessar e baixar o projeto base do nosso curso, para acompanhar com mais eficiência as aulas.

Na página do Git, clique no botão “Code” e selecione a opção “Download ZIP” para baixar o projeto. Recomendamos que teste o projeto e veja se ele apresenta os comportamentos esperados.

Se tiver alguma problema ou dúvida com a instalação, procure ajuda na nossa comunidade no Discord ou no fórum do curso.

https://www.alura.com.br/artigos/como-instalar-configurar-expo-do-react-native?utm_source=gnarus&utm_medium=timeline&_gl=1*map9vo*_ga*MTgwMzIzMjk2Ni4xNjg4ODE5OTcz*_ga_1EPWSW3PCS*MTcwNjA0OTQzNy4xNzIuMS4xNzA2MDQ5NzE1LjAuMC4w*_fplc*c1ZITFluWE8zNjJuNlduJTJGTEhtazQ1VURUdTBkVEVSQThHeThabUx0STlGUW52dUVydlUlMkJJS3dOa3JweG5jbW9LdU9QZWUlMkZpRmE5d1NKS1klMkJteUhiajNQZHQ0MGhyUTFVRkR1c05MemZjeTJEajYxV3JJbnZjZk5sZlNQZHclM0QlM0Q.

https://github.com/alura-cursos/react-native-firebase-notification/tree/projeto-base

https://discord.com/channels/834111810725871677/976563479353901076

@@06
Configurando o projeto no Firebase

Já entendemos o que são o Cloud Messaging e as notificações do tipo Push. Nosso próximo passo é integrar esses recursos em um projeto com React Native. Porém, antes dessa integração, vamos explorar o projeto que utilizaremos neste curso: o SpaceApp.
Explorando o aplicativo
O SpaceApp é o aplicativo com o qual trabalhamos no curso anterior, em que aprendemos sobre storage para fazer upload e download de imagens. Agora, esse aplicativo tem novas telas, vamos conferi-las.

Ao iniciar o SpaceApp no emulador, já temos uma tela nova — a página de login:

Tela de login do SpaceApp. No plano de fundo, há uma imagem parcial do planeta Terra visto do espaço. No centro da tela, temos o logotipo do SpaceApp, seguido dos campos de e-mail e senha e o botão lilás "Entrar"

Essa tela é muito parecida com outras telas de login que desenvolvemos em cursos anteriores. Para checar o código dela no VS Code, basta acessar "src > telas > Login > index.js". Nessa pasta, também consta o arquivo estilos.js com a estilização da página.

No código da tela de login, temos a função logarNaAplicacao() para efetuar o login, utilizando funções de autenticação com Firebase. Na pasta "src > services", temos o arquivo auth.js de autenticação, que desenvolvemos no curso sobre autenticação com Firebase. Esse é um bom exemplo de como podemos reaproveitar código de outros projetos!

O botão "Entrar" é um ActivityIndicator, uma animação de carregamento quando tentamos realizar o login. No aplicativo, vamos inserir o e-mail e a senha cadastrados no console do Firebase anteriormente:

E-mail: andre@gmail.com
Senha: 123456
Ao clicar no botão "Entrar", é possível verificar a animação brevemente onde antes estava escrito "Entrar".

Somos redirecionados para a página principal, onde temos cards sobre fenômenos do universo, dispostos verticalmente em um fundo azul escuro. Na parte superior, temos o logotipo do SpaceApp centralizado. À direita, há um ícone para sair do aplicativo. À esquerda, há um ícone de sino:

Tela principal do SpaceApp, descrita anteriormente na transcrição.

Ao clicar no ícone de sino, somos redirecionados para a tela de notificações. Atualmente, ela está vazia e conta apenas com um fundo azul escuro, o título "Notifications" no topo e o ícone de voltar no canto superior esquerdo.

Nessa tela, exibiremos informações curtas sobre notificações enviadas para esse dispositivos. Elas serão mostradas em formato de card, que é um componente chamado CartaoNotificacao.

Para checar o código desse componente, basta acessar "src > componentes > CartaoNotificacao > index.js" . Esse arquivo é um componente simples, com uma View, uma imagem e alguns textos.

Na pasta "src > telas > Notificacoes", temos os arquivos index.js e estilos.js referentes à tela de notificações. No primeiro, notaremos que temos uma View principal (o fundo azul) e uma ScrollView, que é a área que será possível rolar quando as notificações chegarem.

Configuração para Android
Agora que exploramos o projeto base que utilizaremos, vamos focar em implementar o Push Notification no nosso aplicativo.

Primeiramente, é necessário realizar configurações no console do Firebase. No navegador, vamos abrir o console do Firebase. Assim como fizemos nos cursos anteriores, você precisa ter um projeto criado no Firebase. No caso, criamos um projeto chamado SpaceAppNotificacao e a única edição dele para o do curso anterior é que adicionamos o Authentication e cadastramos um e-mail.

Todos os projetos que fizemos nessa formação, utilizamos o Firebase como um projeto web. Contudo, a parte de notificação em específico precisa lidar com um sistema operacional — Android ou iOS. Ou seja, não conseguiremos usar o projeto web no React Native para enviar notificações.

No menu à esquerda, vamos acessar "Visão geral do projeto". No topo da tela, logo abaixo do nome do nosso projeto, vamos clicar no botão "Adicionar app > Android".

De início, vamos dar um nome ao nosso projeto Android, usando o prefixo "com.". No caso, o chamaremos de "com.spaceapp". Também podemos dar um apelido, mas não é necessário:

Nome do pacote do Android: com.spaceapp
Em seguida, clicaremos no botão "Registar app" e aguardar o processo de criação do projeto Android no console. Uma vez finalizado, aparecerá o botão "Fazer o download de google-services.json" para baixarmos nossas credenciais. Vamos clicar nele. Em seguida, clicaremos no botão "Próxima".

Na sequência, temos instruções de configurações na parte do Android nativo, no entanto, nosso projeto Expo ainda não tem uma parte de Android onde podemos adicionar essas credenciais.

Neste curso, utilizaremos um novo conceito chamado expo-dev-client, que permitirá temos as pastas Android e iOS e continuar trabalhando com Expo. Assim, não precisamos usar o React Native CLI` nesse projeto, mas conseguiremos mexer na parte nativa.

Então, por enquanto, podemos abstrair esse trecho de adição das credenciais. Vamos apenas clicar no botão "Próxima" e, depois, em "Continuar no console". Assim, ativamos a parte do Android. A seguir, vamos repetir o processo para o iOS.

Configuração para iOS
De volta à visão geral do projeto, agora vamos clicar em "Adicionar app > iOS", logo abaixo do nome do nosso projeto. Novamente, usaremos o nome "com.spaceapp":

ID do pacote Apple: com.spaceapp
Após clicar no botão "Registrar app", aguardaremos o processo de criação do aplicativo Apple. Ao finalizar, aparecerá o botão "Fazer o download de GoogleService-Info.plist" para baixarmos os serviços e conseguirmos implementar as notificações no iPhone. Vamos clicar nele, depois em "Próxima".

Na sequência, temos as instruções relativas ao iOS. Vamos pressionar "Próxima". Depois, temos instruções sobre a parte nativa, que ainda não temos acesso. Vamos apenas clicar em "Próxima". Por fim, clicaremos em "Continuar no console".

Chaves de configuração
Agora que fizemos o download das duas chaves de configuração, vamos voltar ao nosso código no VS Code e adicioná-las ao projeto. Basta copiar os arquivos google-services.json e GoogleServices-Info.plist baixados e colá-los na raiz do projeto.

Também precisamos adicioná-las ao nosso arquivo app.json. Primeiramente, vamos inserir algumas configurações na parte do iOS:

// ...

"ios": {
    "supportsTablet": true,
    "googleServicesFile": "./GoogleService-Info.plist",
    "bundleIdentifier": "com.spaceapp"
}

// ...COPIAR CÓDIGO
Assim, conseguiremos conectar o serviço do Firebase com o nosso projeto com React Native. Vamos salvar essas alterações. Em seguida, vamos adicionar configurações na parte do Android, nesse mesmo arquivo:

// ...

"android": {
    "adaptiveIcon": {
        "foregroundImage": "./assets/adaptive-icon.png",
        "backgroundColor": "#FFFFFF"
    },
    "googleServicesFile": "./google-services.json",
    "package": "com.spaceapp"
}

// ...COPIAR CÓDIGO
Vamos salvar as alterações. Agora, conseguimos conectar as nossas credenciais tanto da parte do Android quanto da iOS. A seguir, vamos desenvolver o código para implementar as notificações.

@@07
Utilizando o expo-dev-client

Nosso projeto SpaceApp está com as duas credenciais para trabalharmos com a parte nativa tanto do Android quanto da iOS. Assim, podemos enviar notificações para nosso aplicativo.
Analisando a estrutura de pastas do nosso projeto, notamos que ainda não temos a pasta do Android nem a pasta do iOS para manipular o código nativo. Temos apenas a pasta do Expo, porém não será possível seguir utilizando apenas o Expo.

Existem diferentes formas de trabalhar com a parte nativa do nosso projeto usando React Native.

A primeira forma, a mais famosa e que estudamos em outros cursos é usando o React Native CLI, porém perderíamos todas as facilidades oferecidas pelo Expo. Por exemplo, teríamos que configurar tudo manualmente, além de fazer outras instalações no computador, como o Java.

A segunda forma seria, logo ao criar o projeto Expo, fazer o Eject para deixar de usar o Expo e passar a utilizar o React Native CLI, mas também perderíamos todas as facilidades do Expo e suas bibliotecas.

A terceira forma, mais recente e bastante popular, é usando o expo-dev-client, que usaremos neste curso.

Expo-dev-client
O expo-dev-client é uma maneira de ter "o melhor dos dois mundos". Isto é, teremos a parte do Expo, que facilita toda a configuração de código nativo, e também a parte do código nativo em si.

Ou seja, não vamos fazer o Eject, não vamos trabalhar com o React native CLI, mas teremos a possibilidade de fazer a integração de bibliotecas nativas no nosso projeto com Expo.

No vídeo anterior, quando realizamos as configurações no console do Firebase, passamos direto por seções específicas de configuração da parte nativa. Não precisaremos nos preocupar com essa parte, pois o expo-dev-client se encarregará dela para nós!

Então, vamos acessar a documentação do expo-dev-client. Você pode explorá-la por conta própria, caso queira saber mais sobre esse recurso.

Abaixo do título "Install expo-dev-client", vamos copiar o comando de instalação disponibilizado:

npx expo install expo-dev-clientCOPIAR CÓDIGO
Em seguida, vamos voltar ao nosso projeto no VS Code, abrir o terminal e encerrar a execução da aplicação, com o atalho "Ctrl + C". Em seguida, vamos rodar o comando copiado e aguardar a instalação.

Podemos abrir o arquivo package.json e checar que a biblioteca expo-dev-client foi instalada.

Neste curso, estamos utilizando o expo-dev-client na versão 2.0.1. Recomenda-se o uso da versão mais recente disponível no momento em que você estiver acompanhando o curso. Caso não funcione, você pode utilizar a versão 2.0.1 também. Para especificar a versão desejada, basta adicionar um arroba seguido do número da versão no comando de instalação.
Código de configuração nativa - Android
Apesar de já termos instalado a biblioteca expo-dev-client, o React Native Push Notification ainda não funcionará. Na estrutura de pastas do nosso projeto, ainda não temos as pastas de configuração nativa do Android e do iOS!

Primeiramente, vamos fechar nosso aplicativo no emulador e conferir as aplicações instaladas nele. Com exceção do Expo Go, que é instalado quando executamos nosso projeto em Expo, não temos nenhum aplicativo diferente.

Ao usar o expo-dev-client, teremos um aplicativo específico para o nosso projeto, como se fosse outra aplicação que foi instalada no dispositivo! Ou seja, um aplicativo além do Expo Go.

Para que ele apareça, vamos até o terminal do VS Code e executar o seguinte comando:

npx expo run:androidCOPIAR CÓDIGO
Dessa forma, estaremos rodando o projeto no Android e o código de configuração nativa do Android será criado. Na estrutura de pastas, agora há uma pasta chamada "android" e finalmente temos acesso à parte nativa do nosso projeto! Não precisamos nos preocupar com esse código, por enquanto. O Expo lidará automaticamente com essas configurações.

Esse processo deve levar alguns minutos, porque ele está fazendo o build, então construirá o aplicativo, gerará um executável e o instalará no emulador (ou no dispositivo físico).

Código de configuração nativa - iOS
Neste curso, vamos trabalhar somente com o Android, mas é interessante fazermos alguns comentários sobre o iOS.

Para realizar o mesmo processo para iOS, bastaria usar o seguinte comando:

npx expo run:iosCOPIAR CÓDIGO
Assim, a pasta "ios" seria criada, teríamos acesso ao código nativo também e o aplicativo seria instalado em um dispositivo iPhone.

Para usar notificações no iPhone, há duas ressalvas:

é preciso ter uma conta de pessoa desenvolvedora da Apple para ter acesso a credenciais e usar notificações em aplicativos, até mesmo se você estiver programando nativamente com Swift
para ter uma conta de pessoa desenvolvedora da Apple, atualmente é preciso pagar 99 dólares no plano anual para ter acesso a esses recursos
No Android, não é necessário ter a conta de pessoa desenvolvedora. Conseguiremos utilizar as notificações sem nos preocupar em ter credenciais extras do Google.

Novo aplicativo no emulador
Após a finalização do build, vamos conferir a lista de aplicativos no emulador. Agora, temos um novo aplicativo chamado "react-native-firebase-notification".

Esse novo aplicativo não é o Expo Go, mas ele funciona a partir do Expo que estamos utilizando no projeto. Agora, podemos manipular e instalar bibliotecas na parte nativa e continuamos usando o Expo.

Como demonstração, vamos abrir o aplicativo "react-native-firebase-notification" no emulador. Em seguida, vamos encerrá-lo no terminal do VS Code. Na tela do emulador, notaremos que a conexão com o Expo foi perdida.

Vamos fechar o "react-native-firebase-notification" e tentar abri-lo novamente. Ele não carregará, pois não criamos um APK exclusivo dessa aplicação, ele é uma mistura de código nativo que precisa do Expo para funcionar normalmente.

Para rodar o projeto com Expo, podemos executar o seguinte comando:

npx expo start --dev-clientCOPIAR CÓDIGO
Em seguida, vamos pressionar a tecla "a" e enviar com "Enter". O projeto será aberto no emulador. Podemos fazer o login e o aplicativo funcionará como esperado.

Na sequência, precisaremos instalar outra biblioteca para as notificações funcionarem.

@@08
Faça como eu fiz: utilizando o expo-dev-client

O expo-dev-client é um pacote npm (Node Package Manager) que pode ser instalado em qualquer projeto Expo ou React Native. Com ele você consegue trabalhar com as vantagens do Expo e também utilizar bibliotecas nativas que antes só eram possíveis fazendo eject ou usando o React Native Cli.
Sabendo disso, chegou a hora de praticar!

Para usar o expo-dev-client no projeto, abra o terminal e digite:

npx expo install expo-dev-clientCOPIAR CÓDIGO
Uma vez instalado, abra o emulador ou conecte o seu dispositivo Android no USB do computador e no terminal do projeto digite o comando:

npx expo run:androidCOPIAR CÓDIGO
Esse processo é um pouco demorado, pois ele irá fazer o build do projeto e instalar um aplicativo no seu dispositivo. Quando finalizado o projeto será executado e estará funcionando no seu Android.

Lembre-se que toda vez que instalar uma biblioteca nativa é preciso rodar o comando npx expo run:android para que seja feito o build com as configurações correta da biblioteca.
Uma vez tendo o apk do projeto no dispositivo, sempre que for rodar a aplicação basta digitar:

npx expo start --dev-clientCOPIAR CÓDIGO
E pode escanear o QR code diretamente por esse APK instalado.

O expo-dev-client é uma ferramenta poderosa que permite a gente manter as facilidades da programação mobile usando o Expo, mas com acesso aos recursos de bibliotecas nativas que antes só era possível com o React Native CLI. Dessa forma, vamos conseguir uma biblioteca específica para o Firebase que vai permitir exibir as notificações em nosso aplicativo.
Para saber mais dê uma conferida na documentação oficial.

https://docs.expo.dev/development/create-development-builds/

@@09
Utilizando a biblioteca @react-native-firebase

Estamos começando a trabalhar com a parte nativa do nosso projeto, utilizando Expo. Instalamos o expo-dev-client e notamos que, ao executar o comando npx expo run:android, uma pasta chamada "android" que contém código nativo foi criada no nosso projeto. Sendo assim, é possível utilizar bibliotecas nativas com Expo, que antes só funcionavam no CLI.
Analisando o arquivo package.json, temos a biblioteca firebase instalada no projeto. Esse projeto foi criado como web e conseguimos utilizar vários recursos como autenticação, banco de dados e envio de imagem.

Quando começarmos a usar a parte nativa, é possível que alguns elementos parem de funcionar. Por exemplo, a autenticação parece estar funcionando normalmente e logo notaremos que o envio de imagens também, porém os cards da página principal não apareceram. Então, em breve, faremos alguns ajustes na parte de banco de dados.

Biblioteca React Native Firebase
Para as notificações, precisaremos instalar outra biblioteca, chamada React Native Firebase. Podemos instalar essa biblioteca em projetos com React Native para utilizar diversos serviços do Firebase.

Não a usamos desde o primeiro vídeo da formação porque é preciso trabalhar obrigatoriamente com código nativo, que exige mais configurações. Então, para facilitar nosso aprendizado, optamos por usar a parte que funcionava na web para introduzir os conceitos iniciais sobre uso do Firebase.

Agora que já temos mais conhecimentos de autenticação, banco de dados e envio de imagen, vamos adaptar nosso projeto para funcionar usando o React Native Firebase, utilizando-o nativamente.

Vamos acessar a documentação oficial da biblioteca React Native Firebase, no menu "Getting Started" para conferir as instruções de como instalá-la.

Abaixo do título "Install via NPM", vamos copiar o comando de instalação com NPM:

npm install --save @react-native-firebase/appCOPIAR CÓDIGO
Voltando ao VS Code, vamos abrir o terminal e encerrar a aplicação, caso esteja rodando. Em seguida, vamos executar o comando de instalação da biblioteca e aguardar a finalização desse processo. No arquivo package.json, a biblioteca @react-native-firebase/app constará como instalada.

Neste curso, usa-se a versão 16.5.0 da biblioteca React Native Firebase. Novamente, recomenda-se o uso da versão mais recente disponível no momento em que você estiver acompanhando o curso.
A seguir, vamos focar no Firestore para que o banco de dados volte a funcionar. Vamos acessar a documentação do React Native Firebase, na página Cloud Firestore > Usage, listada no menu à esquerda.

Abaixo do título "Installation", notaremos que será preciso instalar o @react-native-firebase/firestore. Portanto, voltando ao terminal do VS Code, vamos executar o seguinte comando:

npm install @react-native-firebase/firestoreCOPIAR CÓDIGO
Finalizada a instalação, vamos já buscar pelo comando de instalação da parte responsável pelas notificações. No menu à esquerda, vamos acessar a página "Cloud Messaging > Usage" da documentação do React Native Firebase.

Sob o título "Installation", saberemos que é preciso instalar @react-native-firestore/messaging. No VS Code, executaremos o seguinte comando:

npm install react-native-firebase/messagingCOPIAR CÓDIGO
Finalizada a instalação, todas as novas bibliotecas constarão no arquivo package.json. Neste curso, usamos a versão 16.5.0.

Banco de dados
Na sequência, focaremos no banco de dados. Para saber como prosseguir, vamos acessar a documentação na página "Firestore > Usage". Nessa seção, temos instruções de como usar esse serviço.

Primeiramente, é preciso fazer a importação no início do arquivo, com a seguinte sintaxe:

import firestore from '@react-native-firebase/firestore';COPIAR CÓDIGO
No VS Code, vamos acessar "src > servicos > firestore.js". No início desse arquivo, temos as importações que fizemos utilizando o serviço como se fosse um aplicativo web:

import { db } from "../config/firebase";
import { collection, addDoc, getDocs, doc, updateDoc, deleteDoc, query, onSnapshot } from "firebase/firestore";

// ...COPIAR CÓDIGO
Reparamos que o banco de dados não está funcionando atualmente no nosso aplicativo com expo-dev-client, então vamos utilizar essa nova biblioteca que requer código nativo. Vamos fazer a importação:

import { db } from "../config/firebase";
import { collection, addDoc, getDocs, doc, updateDoc, deleteDoc, query, onSnapshot } from "firebase/firestore";

import firestore from '@react-native-firebase/firestore';

// ...COPIAR CÓDIGO
Para testar, modificaremos a função pegarPostsTempoReal() para utilizar a nova biblioteca. Primeiramente, vamos comentar o bloco de código da função, assim poderemos compará-lo com o resultado depois:

// ...

export async function pegarPostsTempoReal(setposts){
    //  const ref = query(collection(db, "posts"))
    //  onSnapshot(ref, (querySnapshot) => {
    //    const posts = []
    //    querySnapshot.forEach(( doc ) => {
    //      posts.push({id: doc.id, ...doc.data()})
    //    })
    //    setposts(posts)
    //  })
}

// ...COPIAR CÓDIGO
Nesse código, nós selecionamos a referência da nossa coleção e depois usamos o onSnapshot(). A seguir, realizaremos o mesmo processo, apenas com outra biblioteca.

Vamos usar as funções firestore() e collection(). A collection é o nome da nossa coleção salva no Firestore, no caso, "posts". Depois, usaremos onSnapshot() e podemos usar o mesmo padrão anterior (querySnapshot), colocando uma arrow function.:

// ...

export async function pegarPostsTempoReal(setposts){
    //  const ref = query(collection(db, "posts"))
    //  onSnapshot(ref, (querySnapshot) => {
    //    const posts = []
    //    querySnapshot.forEach(( doc ) => {
    //      posts.push({id: doc.id, ...doc.data()})
    //    })
    //    setposts(posts)
    //  })
    firestore().collection('posts').onSnapshot((querySnapshot) => {

    })
}

// ...COPIAR CÓDIGO
Dentro da arrow function, usaremos praticamente o mesmo código de antes. Vamos declarar uma constante chamada posts, que será inicializada como um array vazio. Depois utilizaremos o forEach() para fazer um push() de cada documento. Por fim, usamos o setposts():

// ...

export async function pegarPostsTempoReal(setposts){
    //  const ref = query(collection(db, "posts"))
    //  onSnapshot(ref, (querySnapshot) => {
    //    const posts = []
    //    querySnapshot.forEach(( doc ) => {
    //      posts.push({id: doc.id, ...doc.data()})
    //    })
    //    setposts(posts)
    //  })
  firestore().collection('posts').onSnapshot((querySnapshot) => {
    const posts = []
    querySnapshot.forEach(( doc ) => {
      posts.push({id: doc.id, ...doc.data()})
    })
    setposts(posts)
  })
}

// ...COPIAR CÓDIGO
Vamos salvar essas alterações e executar nosso projeto novamente para testá-lo. No terminal do VS Code, rodaremos o seguinte comando:

npx expo start --dev-clientCOPIAR CÓDIGO
Em seguida, pressionaremos a tecla "a" para rodar no Android.

No terminal, aparecerão vários bugs. Nós fizemos o build uma vez para gerar o nosso aplicativo utilizando o código nativo. Contudo, sempre que instalarmos uma biblioteca que exige a configuração do código nativo (como a do Firebase), será necessário fazer o build novamente.

Só precisamos fazer isso uma vez, para fazer o build da configuração inicial. No caso, trata-se da instalação das três bibliotecas:

@react-native-firebase/app
@react-native-firebase/firestore
@react-native-firebase/messaging
Vamos encerrar o aplicativo e fechá-lo no emulador. Em seguida, executaremos o comando para fazer o build:

npx expo run:androidCOPIAR CÓDIGO
Finalizado o build, o sistema abre o aplicativo automaticamente. Também podemos executá-lo manualmente digitando "a" no terminal. Dessa vez, os cards da página principal serão exibidos! Ou seja, a parte da biblioteca que instalamos nativamente já está funcionando.

Vamos conferir a documentação novamente para entender alguns pontos importantes. Na página "Getting Started", temos as instruções de setup do Android e de setup do iOS.

Nessas seções, são mencionados os arquivos GoogleServices-Info.plist e google-services.json que baixamos anteriormente. Além disso, temos instruções de como inserir manualmente alguns códigos na pasta "android" ou "ios", ao rodar o comando run:android ou run:ios.

No entanto, como estamos usando o expo-dev-client, não precisamos fazer essa configuração manualmente na parte nativa! O Expo faz tudo isso automaticamente! Além de facilitar nosso trabalho, é uma ótima forma de evitar erros.

Em resumo, quando rodamos o comando npm expo run:android, o Expo notou que essas novas bibliotecas eram nativas, verificou serem necessárias algumas configurações, entrou nos arquivos específicos e as adicionou automaticamente. Em outras palavras, conseguimos as vantagens do Expo e utilizar recursos nativos.

Já que nosso código está funcionando, vamos remover o trecho de código que comentamos há pouco. Além disso, podemos apagar as importações do Firestore na versão web no início do arquivo:

import { db } from "../config/firebase";
import firestore from '@react-native-firebase/firestore';

// ...

export async function pegarPostsTempoReal(setposts){
  firestore().collection('posts').onSnapshot((querySnapshot) => {
    const posts = []
    querySnapshot.forEach(( doc ) => {
      posts.push({id: doc.id, ...doc.data()})
    })
    setposts(posts)
  })
}

// ...COPIAR CÓDIGO
Adaptações no código
Como utilizaremos outra biblioteca, precisaremos adaptar as demais funções. Em salvarPost(), não utilizaremos mais o addDoc(). Em vez disso, usaremos firestore().collection().add():

// ...

export async function salvarPost(data){
  try {
    const result = await firestore().collection('posts').add(data)
    return result.id
  } catch(error){
    console.log('Erro add post:', error)
    return 'erro'
  }
}

// ...COPIAR CÓDIGO
A função pegarPosts() não é mais necessária, pois vamos recuperar os posts apenas em tempo real. Vamos removê-la.

Na função atualizarPost(), vamos substituir o doc() por firestore().collection().doc().update(). Além disso, podemos remover a constante postRef, já que não a utilizaremos mais, e inserir um await:

// ...

export async function atualizarPost(postID, data){
  try {
    await firestore().collection('posts').doc(postID).update(data)
    return 'ok'
  }
  catch(error){
    console.log(error)
    return 'error'
  }
}

// ...COPIAR CÓDIGO
Por fim, na função deletarPost(), vamos apagar a constante postRef e substituir o deleteDoc() por firestore().collection().doc().delete():

// ...

export async function deletarPost(postID){
  try {
    await firestore().collection('posts').doc(postID).delete()
    return 'ok'
  }
  catch(error){
    console.log(error)
    return 'error'
  }
}
COPIAR CÓDIGO
Agora, não precisamos mais importar o banco de dados no início do arquivo. O arquivo completo ficará assim:

import firestore from '@react-native-firebase/firestore';


export async function salvarPost(data){
  try {
    const result = await firestore().collection('posts').add(data)
    return result.id
  } catch(error){
    console.log('Erro add post:', error)
    return 'erro'
  }
}

export async function pegarPostsTempoReal(setposts){
  firestore().collection('posts').onSnapshot((querySnapshot) => {
    const posts = []
    querySnapshot.forEach(( doc ) => {
      posts.push({id: doc.id, ...doc.data()})
    })
    setposts(posts)
  })
}

export async function atualizarPost(postID, data){
  try {
    await firestore().collection('posts').doc(postID).update(data)
    return 'ok'
  }
  catch(error){
    console.log(error)
    return 'error'
  }
}

export async function deletarPost(postID){
  try {
    await firestore().collection('posts').doc(postID).delete()
    return 'ok'
  }
  catch(error){
    console.log(error)
    return 'error'
  }
}COPIAR CÓDIGO
Vamos salvar todas as alterações. A seguir, vamos testar.

No emulador, vamos adicionar novas postagens, clicando no botão no canto inferior direito. Vamos inserir um título e uma imagem para checar se o recurso de envio de imagem segue funcionando. Ao pressionar o botão "Salvar", teremos uma nova postagem na página principal do aplicativo!

Clicando e segurando o post, podemos conferir mais detalhes. Ao clicar no ícone de lixeira, conseguimos deletá-lo. Nosso código está funcionando como esperado.

Agora, temos acesso ao Firestore para ter recursos nativos, como de notificação. Na próxima aula, começaremos a usar as notificações.

@@10
Faça como eu fiz: configuração do projeto e instalação da biblioteca @react-native-firebase

Caso você não tenha o projeto do Firebase, acompanhe o passo a passo da documentação ou confira este vídeo do curso de Firebase Authentication.
Com tudo pronto, siga os seguintes passos:

Crie o banco de dados firestore no console do Firebase, para armazenar os posts;
Crie o banco dados para armazenamento de arquivos com o Cloud Storage, no console do Firebase;
Modifique o arquivo firebase.js na pasta config para configurar o aplicativo.
E para conseguir utilizar o Firebase Cloud Messaging:

Instale a biblioteca nativa react-native-firebase. Você pode seguir o passo a passo fornecido na própria documentação.

https://firebase.google.com/docs/firestore/quickstart#create

https://cursos.alura.com.br/course/react-native-autenticacao-firebase/task/118027

https://rnfirebase.io/#installation

A configuração do arquivo firebase.js é muito similar ao que já foi feito nos cursos anteriores e ficará conforme o código abaixo:
import { initializeApp } from "firebase/app";
import { getFirestore } from 'firebase/firestore';
import { getStorage } from 'firebase/storage';
import { API_KEY, AUTH_DOMAIN, PROJECT_ID, STORAGE_BUCKET, MESSAGING_SENDER_ID, APP_ID } from "@env"

const firebaseConfig = {
  apiKey: API_KEY,
  authDomain: AUTH_DOMAIN,
  projectId: PROJECT_ID,
  storageBucket: STORAGE_BUCKET,
  messagingSenderId: MESSAGING_SENDER_ID,
  appId: APP_ID
};

// Inicializa o Firebase
const app = initializeApp(firebaseConfig);

// Inicializa o Firestore
const db = getFirestore(app);

const storage = getStorage(app)

export { db, storage };COPIAR CÓDIGO
Lembre-se que uma vez feita a instalação da biblioteca nativa, é preciso executar o comando de build abaixo para poder funcionar como esperado:

npx expo run:android

@@11
O que aprendemos?

A primeira aula foi finalizada, parabéns!!! E nela você aprendeu que o Firebase Cloud Messaging (FCM) é um sistema de mensagens em nuvem que permite enviar notificações push para dispositivos móveis.
Sobre o FCM, você também aprendeu como:

Configurar o FCM no console do Firebase;
Integrar o FCM em um projeto React Native;
Instalar a biblioteca nativa react-native-firebase;
Instalar, configurar e utilizar expo-dev-client.
Muito bem! Vamos para a nossa próxima aula?