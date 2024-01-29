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

#### 27/01/2024

@02-Projeto Web e notificações

@@01
Projeto da aula anterior

Você pode revisar o seu código e acompanhar o passo a passo do desenvolvimento do nosso projeto e, caso deseje, pode baixar o projeto da aula anterior.
Bons estudos!

https://github.com/alura-cursos/react-native-firebase-notification/tree/aula1

@@02
Envios com Cloud Messaging

Já fizemos diversas configurações no nosso aplicativo e agora podemos ter acesso ao código nativo usufruindo de todos os recurso do expo utilizando o expo dev client. Então instalamos a biblioteca do Firebase, que utiliza recursos nativos, como o de notificação, mas até o momento só utilizamos para manipular nosso banco de dados no Firestore, como já fazíamos anteriormente.
Para descobrirmos como receber as notificações, podemos acessar a documentação "Cloud Messaging" do React Native Firebase, que foi a biblioteca que instalamos. No menu da esquerda, temos a seção "Cloud Messaging" (Mensagens na Nuvem) e nós já fizemos a preparação que consta na subseção "Installation" (Instalação), com a instalação da biblioteca.

Em seguida, temos a subseção "Usage" (Uso), explicando que para usarmos precisamos de algumas permissões. Porém isso é para o iOS, o Android, por padrão, já permite receber notificações, então não precisamos da autorização do usuário para permitir isso.

Ainda assim, é sempre bom termos o trecho de código que aparece na documentação caso queiramos usar em Iphones, então aproveitaremos o código que ela está oferecendo para adicionarmos à aplicação:

import messaging from '@react-native-firebase/messaging';

async function requestUserPermission() {
  const authStatus = await messaging().requestPermission();
  const enabled =
    authStatus === messaging.AuthorizationStatus.AUTHORIZED ||
    authStatus === messaging.AuthorizationStatus.PROVISIONAL;

  if (enabled) {
    console.log('Authorization status:', authStatus);
  }
}COPIAR CÓDIGO
Copiado esse código, faremos o teste diretamente na tela principal da nossa aplicação. Para isso navegaremos para "src > telas > Principal > index.js".

No arquivo "index.js", adicionaremos a função que copiamos da documentação dentro da função Principal(), abaixo dos construtores. Em seguida, passaremos a importação para o lado de fora, logo abaixo da importação do { logout }.

E a função que colamos não está sendo chamada ainda, então faremos isso nos useEffect, que vai rodar apenas um vez para pedirmos a permissão do usuário. Feitas essas alterações, podemos salvar.

//código omitido

import messaging from '@react-native-firebase/messaging';

export default function Principal({ navigation }) {
    const [posts, setPosts] = useState([]);
    const [notifications, setNotifications] = useState([]);

    async function requestUserPermission() {
      const authStatus = await messaging().requestPermission();
      const enabled =
        authStatus === messaging.AuthorizationStatus.AUTHORIZED ||
        authStatus === messaging.AuthorizationStatus.PROVISIONAL;

      if (enabled) {
        console.log('Authorization status:', authStatus);
      }
    }

    useEffect(() => {
        pegarPostsTempoReal(setPosts);

        requestUserPermission();
    }, [])

//código omitidoCOPIAR CÓDIGO
Notem que al salvarmos, nada muda no emulador, mas no Terminal aparece a mensagem "Authorization Status: 1" (Status de Autorização: 1). Se o status é "1", quer dizer que está autorizado para receber a notificação, então está tudo preparado para receber mensagens.

E como recebemos essas mensagens? Para descobrir, continuaremos lendo a documentação do Cloud Messaging. Acessando a subseção "Foreground state messages" (Mensagens de estado de primeiro plano), temos instruções de como ter uma função simples para receber essas mensagens.

Inclusive temos um exemplo de código em que a função foi criada dentro de um useEffect para receber as mensagens. Então usaremos a mensagem do exemplo para descobrir como ela chega no nosso dispositivo.

import React, { useEffect } from 'react';
import { Alert } from 'react-native';
import messaging from '@react-native-firebase/messaging';

function App() {
  useEffect(() => {
    const unsubscribe = messaging().onMessage(async remoteMessage => {
      Alert.alert('A new FCM message arrived!', JSON.stringify(remoteMessage));
    });

    return unsubscribe;
  }, []);
}COPIAR CÓDIGO
Voltaremos para o código e dentro do useEffect, logo após a chamada de requisição, escreveremos messaging.onMessage(mensagem => {console.log(mensagem)}). Então quando deixaremos ela em uma arrow function, fazendo um console.log() dessa mensagem. E como precisamos que a mensagem toda chegue, transformamos a arrow function em assíncrona, escrevendo async.

//código omitido
    useEffect(() => {
        pegarPostsTempoReal(setPosts);

        requestUserPermission();

        messaging().onMessage( async mensagem => {
            console.log(mensagem)
        })
    }, [])COPIAR CÓDIGO
Salvamos o código e, com isso, nada acontece ainda, além da impressão da autorização novamente. Para testarmos e descobrirmos se a mensagem chega, podemos usar o console do Firebase.

Portanto, acessaremos o site do Firebase e no menu da esquerda acessaremos "Engajamento > Messaging". Essa opção abre uma nova tela do lado direito, onde podemos criar campanhas para enviar mensagens para o dispositivo.

Clicaremos no botão branco "Crie sua primeira campanha", que fica logo abaixo do título e descrição sobre o Messaging, na parte superior esquerda da tela. Com isso, uma janela pop-up com o título "Integração de mensagem do Firebase" abre, e nela tem duas opções: enviar campanhas para qualquer dispositivo, ainda que fechados, ou apenas para os dispositivos abertos no momento.

Escolheremos a primeira opção, ou seja, enviar para qualquer dispositivo, e clicaremos depois no botão "Criar" no canto inferior direito dessa janela. Uma nova tela surge contendo a primeira página de um formulário. Nela tem de duas colunas e o título "Notificação". No lado esquerdo do formulário temos os campos para serem preenchidos e no esquerdo a visualização do dispositivo.

O primeiro campo que preencheremos é o "Título da notificação", com o título da mensagem, que será "titulo teste". O segundo campo é o texto da notificação, que será "Enviando mensagem".

No campo seguinte podemos adicionar o link de uma imagem, se quisermos, mas deixaremos vazio. O último campo é o "Nome da notificação", que é opcional e não precisamos no momento.

Preenchidos os campos necessários, clicaremos no botão "Próximo", no canto inferior esquerdo do formulário. Com isso, mudamos para segunda página do formulário, que é a "Segmentação", onde precisamos escolher para quais pessoas usuárias queremos disparar a mensagem.

Nessa página temos o campo "Segmentar usuário se...", que é dividido em dois. Na metade da esquerda temos escrito "App" e na direita podemos escolher entre enviar para todos dispositivos Android, todos os iOS e para Web. Escolheremos a primeira opção, que é a Android, que estamos utilizando neste curso.

Abaixo do campo tem um hiperlink com "Segmentar outro App", e se clicarmos nele podemos adicionar outras plataformas. No nosso caso, não precisaremos, portanto clicaremos no botão "Próxima", abaixo do hiperlink.

A página seguinte é a "Programação", com o campo "Enviar para usuários qualificados" preenchido com "Agora". É o que queremos, então podemos clicar no botão "Próxima" abaixo desse campo.

Assim chegamos na última página do formulário, que é a "Outas opções (opcional)". Como é opcional, podemos deixar os campos iniciais vazios e, o último campo, que é o "Vencimento", também tem duas opções: a primeira é de números e a segunda de medida de tempo.

A opção de vencimento ficou como "4 semanas", então depois disso, se o dispositivo não receber, ele não receberá mais. Então suponhamos que o celular desligou ou acabou a bateria. A mensagem ainda vai chegar, porque ela tem um prazo de vencimento de 4 semanas.

Ao finalizarmos, clicamos em "Revisar" no canto inferior direito do formulário, o que abre a janela pop-up "Revisar mensagem". Ao confirmarmos o conteúdo exibido, clicamos em "Publicar", no canto inferior direito da janela. Assim, no canto superior direito aparece a mensagem "A campanha foi iniciada com sucesso".

Ao aguardarmos um pouco, a tela atualiza e aparece uma tabela com os dados da mensagem que criamos. Essas campanhas que mandam mensagem para o dispositivo não chegam necessariamente em tempo real, então já disparamos a mensagem mas, ao voltarmos para o VS Code, percebemos que nada aconteceu no nosso projeto.

Essa mensagem pode demorar até alguns minutos para chegar, então precisamos aguardar esse processo terminar para recebermos a mensagem no nosso Terminal.

[Um efeito sonoro toca enquanto uma tela de carregamento aparece no vídeo]
Passado um tempo a mensagem chega, no meu caso, demorou quase 5 minutos para chegar essa mensagem. Então estejam cientes que essa mensagem pode demorar para chegar, porque são campanhas e não precisamos, necessariamente, que a pessoa usuária seja notificada de imediato.

Caso quiséssemos que a mensagem chegasse mais rápido, poderíamos enviar uma mensagem diretamente para o dispositivo. Podemos fazer isso através de um token que o próprio Firebase oferece, e para acessá-lo criaremos a função pegarToken antes do useEffect.

    async function pegarToken(){
        const token = await messaging().getToken()
        console.log(token)
    }COPIAR CÓDIGO
Nessa função criamos a variável token, contendo o método .getToken, e um console.log(token) para visualizarmos o token. Em seguida podemos chamar essa função no useEffect após as permissões.

//código omitido

    useEffect(() => {
        pegarPostsTempoReal(setPosts);

        requestUserPermission();

        pegarToken()

        messaging().onMessage( async mensagem => {
            console.log(mensagem)
        })
    }, [])COPIAR CÓDIGO
Salvamos o código e, com isso, aparece no Terminal várias letras e números. Esse é nosso token, com o qual garantimos que o dispositivo do emulador com esse aplicativo é único.

Então copiaremos esse token e voltaremos para o Console do Firebase, onde ainda estamos na tela de Messaging, com a tabela de informações da campanha que criamos. Vamos excluir essa campanha.

Para isso, ao final dos dados, na extrema direita da tabela, tem um ícone com três pontos verticais, onde clicaremos. É aberto um menu com as opções "Copiar" e "Excluir". Clicamos em "Excluir" e uma janela pop-up abre no centro da tela. No canto inferior direito dessa janela tem um botão vermelho escrito "Excluir" onde clicaremos.

Com isso, voltamos para primeira tela que vimos na seção "Messaging". Clicaremos novamente no botão branco "Crie sua primeira campanha". Mais uma vez a janela pop-up é aberta no centro da tela, onde escolheremos a primeira opção e clicaremos no botão branco "Criar" no canto inferior direito.

Na primeira página do formulário, preencheremos o título como "dispositivo teste" e o texto da notificação como "corpo da mensagem". Depois, ao invés de clicarmos para criar a campanha, clicaremos no botão azul "Enviar mensagem de teste", que fica na parte superior da coluna direita na primeira página do formulário.

Ao clicarmos no botão, abrimos a janela pop-up "Testar no dispositivo" no centro da tela. Nela já temos um token adicionado na parte inferior da janela, mas adicionar outro.

Iremos colar o token que copiamos no primeiro campo da janela e clicaremos no botão com o "+" no lado direito desse campo. Em seguida, clicamos na caixa de seleção no lado esquerdo do token que adicionamos para selecioná-lo. Por fim, clicamos em "Testar" no canto inferior direito da janela.

Voltando para o VS Code, observamos no Terminal que a mensagem já foi exibida de imediato. Entretanto, saibam que esse teste pode levar alguns segundos para enviar a mensagem também, então não é instantâneo, mas é bem mais rápido que uma campanha, como testamos anteriormente.

Na mensagem que chega, temos algumas seções, como a ""body": "corpo da mensagem"", que foi o que escrevemos, e o ""title": "dispositivo teste"". Ao observarmos a mensagem que chegou na campanha anterior também tínhamos algumas informações, no caso a ""body": "enviando mensagem"" e o ""title": "titulo teste"".

Vimos como testar a notificação. Ainda não a exibimos na parte superior do dispositivo, mas conseguimos enviar dados do Cloud Messaging. Fizemos tudo isso usando o Console do Firebase, mas essa não é a única forma de dispararmos mensagem. Aprenderemos mais sobre isso no próximo vídeo.

https://rnfirebase.io/messaging/usage

@@03
Faça como eu fiz: envios com o Cloud Messaging

Chegou a hora de praticar o que aprendemos em aula. Vamos lá?
Na tela principal do projeto, dentro de uma useEffect, crie as seguintes funções para poder receber as notificações em seu App:

requestUserPermission() → Essa função vai solicitar o acesso do dispositivo para receber notificações;
Use o messaging().onMessage() para observar as notificações que forem disparadas.
Para ser possível o recebimento de notificações é necessário que o dispositivo conceda a permissão. No geral, a maioria dos dispositivos Android já permitem receber notificações sem precisar solicitar, mas nos iPhones não. Então por isso é bom garantir que o nosso App solicite essa permissão para todos usando a função requestUserPermission().

Para fazer a função requestUserPermission() adicione o seguinte código:
async function requestUserPermission() {
  const authStatus = await messaging().requestPermission();
  const enabled =
    authStatus === messaging.AuthorizationStatus.AUTHORIZED ||
    authStatus === messaging.AuthorizationStatus.PROVISIONAL;

  if (enabled) {
    console.log('Authorization status:', authStatus);
  }
}COPIAR CÓDIGO
Para ouvir as mensagens, adicione o seguinte código no useEffect:

requestUserPermission();

pegarToken();

messaging().onMessage( async mensagem => {
  console.log(mensagem)
});COPIAR CÓDIGO
Essa função pegarToken é importante para que você tenha acesso ao token do dispositivo e consiga dispara uma notificação para ele diretamente do console do Firebase, assim como vimos na aula. O código da função pegarToken é:

async function pegarToken(){
    const token = await messaging().getToken()
    console.log(token)
}COPIAR CÓDIGO
Se quiser saber como fica o código completo, dê uma conferida nesse repositório do projeto.

@@04
Preparando o ambiente: projeto base da versão web

Nas próximas videoaulas baixar e utilizar o Projeto Web e para que você possa acompanhar e colocar em prática de todo o processo, sugerimos que você faça o donwload do projeto web ou ou acesse por esse github.

https://github.com/alura-cursos/spaceapp-web/archive/4cd7dd2c7c659f977d77ed2a99d0afe1b121461c.zip

https://github.com/alura-cursos/spaceapp-web/tree/4cd7dd2c7c659f977d77ed2a99d0afe1b121461c

@@05
Baixando e configurando o projeto web

Finalmente conseguimos enviar notificações para nosso dispositivo, mas fizemos isso através do Console do Firebase. Existe outra forma de fazermos isso, inclusive ao observarmos a seção "Visão geral da arquitetura FCM" da documentação do Firebase temos mais informações sobre o envio de notificações. Nessa documentação há uma imagem que nos auxilia a entendermos melhor esse funcionamento.
Diagrama presente na documentação do Firebase para exemplificar o envio de mensagens. Nele existe 4 colunas numeradas. A coluna número 1 é a "Message building and targeting" ou seja "Construção e segmentação de mensagens". Nela existe duas imagens: uma que lembra o console do Firestore representando as "Notifications Console GUI" e a segunda representando o "Trusted Enviroment", que é um retângulo contendo dois outros retângulos, um escrito "Admin SDK" e outro escrito "HTTP/XMPP". A coluna de número 2 é a "FCM backend" e tem o ícone do Firebase Storage. A coluna 3 é a "Plataform-level message transporte". Nela tem três retângulos cada um com um texto, sendo eles: "Android transport layer", "iOS / APNs" e "Web Push". A coluna de número 4 é a "SDK on device" e contém o ícone de três aparelhos. O primeiro representa um smartphone Android, o segundo representa um Iphone e o terceiro representa um notebook. Da coluna 1 saem duas setas: uma da "Notifications Console GUI" e outra da "Trusted Enviroment", ambos apontando para o ícone do Firebase na coluna 2. Entre as setas está o texto "Send to topic or instance". Do ícone da coluna 2 saem três setas, cada uma apontando para um dos retângulos da coluna três. E da coluna três sai uma seta de cada retângulo: o do primeiro aponta para o dispositivo Android, do segundo aponta para o Iphone e do terceiro aponta para o notebook.

Para disparar as mensagens para um dispositivo existem duas formas. A primeira é a que utilizamos, representada na imagem pelo "Notifications Console GUI" (Notificações pelo Console GUI). Então usamos o Console do Firebase para digitarmos o título, corpo e até adicionamos uma imagem à mensagem.

Essa mensagem é disparada para o back-end dos serviços do Firebase Cloudstore, representados na coluna 2. Esse back-end vai descobrir para quem enviar a mensagem: um dispositivo Android, iOS ou Web, representados na coluna 3. Por fim ele envia para o dispositivo, representado na coluna 4, onde conseguimos ver e mostrar a mensagem no Console.

Entretanto, outra forma que existe é por meio de uma requisição HTTP, onde precisamos, basicamente, criar uma API nossa, que terá um código elaborado da forma que acharmos necessário para nossos projetos. Essa API dispara para o back-end do Firebase Cloud Message (FCM), que será, posteriormente, responsável por enviar a mensagem para o dispositivo.

Tendo acesso à API que podemos criar, podemos utilizá-la para disparar mensagens por meio de um site que criarmos ou até mesmo usar um dispositivo para enviar uma mensagem para essa API e dela disparar para diversos outros dispositivos. Para esse curso usaremos uma aplicação web que fará exatamente isso.

Essa aplicação Web irá se comunicar com uma API que iremos construir e essa API irá se comunicar com o back-end do Firebase Cloud Message. Entretanto, como mostra a imagem, não conseguimos enviar diretamente para o back-end do FCM, por isso precisamos construir essa API.

O projeto dessa API será disponibilizado por meio de atividades. Então iremos acessar o repositório spaceapp-web, onde conseguimos baixar o projeto da API em formato ZIP clicando no botão verde escrito "Code" no canto superior direito e depois em "Download ZIP".

Feito isso, basta extrair o código no seu computador e, depois, abri-lo no VS Code ou na IDE que preferir. Fazendo isso vocês terão acesso à pasta do projeto.

Para instalar as dependências, abram o Terminal da IDE e digitem npm install, pressionando "Enter" em seguida. Desse modo todas as dependências necessárias para rodar o projeto serão baixadas.

Quando o download acaba, precisamos fazer algumas configurações, como modificar o código ".env.local", que acessamos clicando na coluna da esquerda. Caso não encontrem esse arquivo, é porque ele não fica salvo no GitHub.

Nesse caso vocês precisarão criá-lo, clicando com o botão direito na coluna esquerda e selecionando "Novo arquivo". Em seguida, escrevam ".env.local". Dentro desse arquivo vocês escreverão:

NEXT_PUBLIC_API_KEY=""
NEXT_PUBLIC_AUTH_DOMAIN=""
NEXT_PUBLIC_PROJECT_ID=""
NEXT_PUBLIC_STORAGE_BUCKET=""
NEXT_PUBLIC_MESSAGING_SENDER_ID=""
NEXT_PUBLIC_APP_ID=""COPIAR CÓDIGO
Dentro das aspas, logo após o igual, adicionaremos chaves que são obtidas diretamente no Console do Firebase. Portanto nós retornamos ao Firebase e no canto superior direito da coluna da esquerda, clicaremos no ícone de engrenagem, onde estão as "Configurações do projeto".

Depois rolamos até o final onde, na última seção tem um menu, com a opção "Apps da Web". Ao clicarmos no arquivo deles, rolamos novamente para baixo e encontraremos um trecho de código com todas as chaves identificadas pelo nome. Basta copiá-las e adicioná-las ao ".env.local".

Além disso, precisamos fazer outra configuração. Navegando para "src > config", notamos que ela é bem similar ao que fizemos no projeto com React Native.

A diferença é que além do arquivo "firebase.js", também bastante similar ao que fizemos anteriormente, tem o arquivo "firebaseAdmin.js". Ele contém uma biblioteca do Firebase Admin, para disparar notificações para nosso dispositivo, e acessa a serviceAccountKey.json, que é outro arquivo dentro da pasta "config" contendo diversas chaves de acesso.

Vocês devem baixar o projeto com as chaves que estou usando, mas elas não irão funcionar, porque irei excluir esse projeto após a finalização do curso. Então vocês precisarão substituir o conteúdo desse arquivo.

Para isso, voltaremos ao Console do Firebase para acessarmos a parte de administração. Então no topo da tela "Configurações do projeto", acessaremos a quarta aba, que é a "Contas de serviço". Nessa aba, teremos uma tela com um menu do lado direito e as seções do lado esquerdo.

No menu está selecionado o "SDK Admin do Firebase", que está aberto do lado esquerdo com a opção "Node.js" selecionada. Abaixo das opções, tem uma caixa com o código de acesso para aplicações, no caso, Node.js, e depois dessa caixa de código tem um botão azul escrito "Gerar nova chave privada".

Clicando nesse botão, uma janela pop-up abre no centro da tela com uma mensagem e, no canto inferior direito, um botão azul com ícone de download escrito "Gerar chave". Clicando nele vocês baixam as chaves, que ele irá gerar com um nome estranho.

Nesse caso vocês podem renomear para o nome "serviceAccountKey.json", como está no projeto, ou extrair todo o conteúdo que ele baixar e substituir pelo arquivo que já está no projeto. Feito isso, conseguimos executar nossa aplicação, então abrimos o terminal, digitamos "npm run dev" e pressionamos "Enter".

Em seguida, podemos abrir no navegador e escrever "localhost:3000" . Ao pressionarmos "Enter", notamos que ele abre uma aplicação Web que se conectou com nosso serviço do Firebase e baixou os posts que tínhamos criado. Clicando em algum post, temos acesso às informações que podemos editar e salvar, além de, no canto inferior direito da janela, termos o botão de criar um novo post.

Para testarmos, vamos clicar em uma das imagens com o botão direito do mouse e selecionar a opção "Copiar o endereço da imagem". Em seguida, clicaremos no botão do canto inferior direito da janela e criaremos um novo post para descobrir se ele aparece diretamente na aplicação do emulador.

Clicando no botão para criar um novo post, uma janela pop-up com o formulário aparece no centro da tela. Nesse caso, preencheremos os campos de "Título", "Fonte" e "Descrição" como "teste" e colaremos o link da imagem no último campo, clicando no botão "Salvar" ao final da janela pop-up.

Ao salvarmos o post, notamos que ele cria um novo post. E como estamos usando o recurso em tempo real do Firestore, apareceu ao mesmo tempo tanto na página web quanto no Mobile, o que é bem legal.

A única coisa que não conseguimos fazer na Web é excluir um post, então clicaremos no post "teste" no dispositivo e depois no ícone da lixeira, no canto superior direito. Fazendo isso, o post é excluído do aplicativo e da página web, então vimos que está funcionando.

Inclusive se clicarmos no post de "Lua" na página Web e editarmos o título para "Lua 2", ele atualiza na hora no Mobile também. Ao voltarmos o nome do post para "Lua" novamente ele é atualizado mais uma vez nas duas aplicações. Portanto façam o teste para descobrir se está funcionando e se o seu projeto se conectou corretamente aos dados do Firebase.

Agora vamos explorar rapidamente o código dessa aplicação, começando pela pasta "src", que tem pastas muito similares às que criamos no projeto de React Native. Então temos uma pasta "componentes" que tem outras pastas com os arquivos dos nossos componentes.

Por exemplo em "componentes > CartaoPost" temos um arquivo "indes.js" com uma função CartaoPost recebendo alguns parâmetros. Entretanto, ao invés da View do React Native, estamos utilizando div e, ao invés de text, o h1 e h2. Essa é, basicamente, a sintaxe do HTML, mas não precisamos nos preocupar muito, porque focaremos apenas na construção da API.

Em seguida, em "src" temos a pasta "config", onde já passamos por todos os arquivos. Depois temos a pasta "pages" (páginas), contendo a pasta "api" e três arquivos: o "_app.js", o "_document.js" e o "index.js".

A pasta "api" por enquanto está vazia, mas é onde criaremos nossa API. O arquivo "_app.js" contém a função principal da nossa aplicação. O "_document.js" tem alguns outros dados da aplicação. Por fim o "index.js" é o arquivo principal, com uma lista de posts.

Nós não iremos nos preocupar muito com isso, mas percebam que tem muita similaridade. E como estamos usando para um projeto Web, usamos o NextJS, um framework que trabalha com React, que é muito parecido com o React Native.

Outra pasta da "src" e a "sevicos", onde temos o arquivo "firestore.js", contendo a mesma função que fizemos no React Native. Notem que com isso a pessoa cliente pode reaproveitar nos projetos.

Por fim, na pasta "src", contemos a "styles" (estilos) com a pasta "componentes". Nessa pasta tem dois arquivos com o CSS da nossa aplicação, o 'globals.css" e o "Home.module.css", parecido com o que fazemos no React Native usando o stylesheet.

Os outros arquivos do projeto são apenas de configurações, então não precisamos nos preocupar com eles e nem os explorar. E agora que temos uma noção melhor do projeto web que utilizaremos no curso, no próximo vídeo descobriremos como construir nossa API.

https://github.com/alura-cursos/spaceapp-web/tree/main

https://github.com/alura-cursos/spaceapp-web/archive/refs/heads/main.zip

@@06
Criação do servidor de notificações

Agora que já exploramos o projeto Web, entendemos como ele funciona e como executá-lo, assim como fizemos as configurações para ele funcionar corretamente, descobriremos como criar a API.
A primeira coisa que faremos é abrir o projeto Web e navegar para "src > pages", onde encontramos a pasta "api". Ela está vazia, e nós criaremos nossa API dentro dela. Para fazemos um teste, criaremos um novo arquivo dentro dessa pasta, chamado "spaceapp.js".

Esse arquivo será a rota da nossa API para enviarmos e recebermos algum tipo de informação. Para criar a API, criaremos uma função assíncrona chamada handler, porque é a forma que ele reconhece a função. Então na linha 2 desse arquivo escreveremos:

export default async function handler(){}COPIAR CÓDIGO
Essa é a sintaxe do NextJS, mas é uma forma de criarmos a API diretamente dentro de uma aplicação Web. Isso torna muito mais fácil de salvarmos nosso projeto em algum lugar, ao invés de salvarmos no servidor, depois na aplicação Web e depois na Mobile. Dessa forma seriam três coisas distintas, mas como estamos fazendo temos ao menos Web e servidor juntos.

Dentro da função handler(), receberemos dois parâmetros: o req e o res. O req representa a requisição que faremos, ou seja, a chamada para essa função, enquanto o res vem da resposta que daremos. Então fica handler(req, res).

Por enquanto não enviaremos nada, então deixaremos o req vazio, já o res será o que mostraremos para o usuário quando chamarmos essa função. Nesse caso será res.status(200), então se ele conseguir chamar a função, retornaremos um status 200, que é o sucesso.

Dica: Quando um site é carregado e retorna um status 200, ele indica que tudo ocorreu como o esperado. Já se o status retornado for o 404 ou 503 indica que ocorreu algum problema. Nesse curso não focaremos muito no significado dos status.
Além disso, podemos retornar um json(). Nós já aprendemos e trabalhamos com JSON, e esse conterá o código status: 'API está funcionando!'. Portanto fica:

export default async function handler(req, res){
    res.status(200).json({
        status: 'API está funcionando!'
    })
}COPIAR CÓDIGO
Salvamos esse código, agora precisamos testar se ele funciona, voltando para nossa aplicação na Web. Na barra de endereço, onde está "localhost:3000", escreveremos agora "localhost:3000/spaceapp", que é o nome do arquivo que criamos. Ao pressionarmos "Enter", uma faixa preta aparece no centro da janela e, no centro dela, temos a mensagem "404 | This page could not be found" (404 | Esta página não pôde ser encontrada).

Ela não foi encontrada porque esquecemos um detalhe no endereço: o "/api" entre o "localhost" e o "spaceapp". Então o endereço correto é: "localhost:3000/api/spaceapp". Ao pressionarmos "Enter", ele exibe no navegador a mensagem que escrevemos:

{
"status": "API está funcionando!"
}

Com poucas linhas de código, criamos uma API que está funcionando. Caso o seu navegador não tenha aberto a mensagem colorida da mesma forma que a minha, ou seja, o "status" em azul e o "API está funcionando!" em amarelo, é por causa de uma extensão que eu tenho instalada no meu navegador, chamada "JSON Viwer". Vocês podem baixar e utilizar, ou podem deixar sem, mas ela não estará colorida.

Nossa API está funcionando, mas não temos uma comunicação para enviar uma mensagem para nosso aplicativo. Para fazermos isso, começaremos importando a variável admin, vinda do "config > firebaseAdmin.js". Essa variável é responsável por disparar essas mensagens para o Firebase Cloud Messaging. Sendo assim, escreveremos na primeira linha import { admin } from '../../config/firebaseAdmin';.

Tendo acesso à função Admin, precisamos criar um método dentro da handler() para disparar as mensagens. Para isso, iremos nos basear no que a documentação nos fornece de informação.

Então abriremos a documentação do Firebase e, no menu da esquerda, ao final da seção de "Cloud Messaging", acessaremos "Ambiente de servidor > Criar solicitações de envio". Acessando a página "Criar solicitações de envio do servidor de aplicativos", temos um exemplo para Node.js, e estamos fazendo uma API que utilizará o Node.

// This registration token comes from the client FCM SDKs.
const registrationToken = 'YOUR_REGISTRATION_TOKEN';

const message = {
  data: {
    score: '850',
    time: '2:45'
  },
  token: registrationToken
};

// Send a message to the device corresponding to the provided
// registration token.
getMessaging().send(message)
  .then((response) => {
    // Response is a message ID string.
    console.log('Successfully sent message:', response);
  })
  .catch((error) => {
    console.log('Error sending message:', error);
  });COPIAR CÓDIGO
Nesse exemplo, para enviarmos uma notificação, precisamos no token do dispositivo, e já temos acesso a esse token. Depois precisamos criar uma mensagem e usar o getMessaging().send(mensagem), para enviar a mensagem para nosso dispositivo.

Então podemos criar uma mensagem assim e descobrir o que acontece. Para isso, podemos copiar a mensagem de teste que a documentação nos mostra, voltar para o "spaceapp.js" e colar o código na linha 5, mudando de message para mensagem.

const mensagem = {
  data: {
    score: '850',
    time: '2:45'
  },
  token: registrationToken
};COPIAR CÓDIGO
Observação: A princípio o instrutor corrige para message ao invés de mensagem, mas na transcrição manteremos a escrita correta desde o começo.
Precisamos do nosso token na linha 10, no lugar de registrationToken. Para acessarmos o token, copiaremos do nosso projeto em React Native. Então executaremos o projeto, esperamos o token carregar no terminal e copiaremos ele. Em seguida, voltamos para o código da API e colamos no campo token, dentro de uma string.

  const mensagem = {
    data: {
      score: '850',
      time: '2:45'
    },
    token: 'fymAfwTZRMyfanSMZ_hRPx:APA91bGfQi_x-VFhAOO0Ly8BjJznceBpmCZUg7a65d3-iDTY8PDUfjlumpU6jV_gAZH50VrLxGWG-DN__1sbT-O5vH3F56SuroWPVsZW73M3rb4M94WOvePQq0arqKdc9AbQLnDgNWwN'
  };COPIAR CÓDIGO
Salvamos esse código e, feito isso, precisamos enviar essa informação. No exemplo da documentação foi usado o then/catch, mas usaremos o try/catch para pegar erros. Com isso, podemos tentar enviar a mensagem dentro do try.

try {
    await admin.messaging().send(mensagem)
    console.log('Notificacao enviada com sucesso!')
    res.status(200).json({
        status: 'Notificacao enviada com sucesso!'
    })
}
catch(error){
    console.log(error)
    res.status(400).json({
        status: 'Erro ao enviar'
    })
}COPIAR CÓDIGO
Então no try usamos o await para esperar a mensagem, depois usamos o admin.messaging().send(), passando a mensagem. Caso consigamos enviar, fazemos um console.log() com a mensagem "Notificação enviada com sucesso!" e retornamos o res. Isso porque precisamos do res para retornar o status, que nesse caso também é "Notificação enviada com sucesso!".

Quando não conseguimos enviar, fazemos um console.log do erro e retornamos outro res.status(), dessa vez com o status 400 a mensagem "Erro ao enviar". E como já adicionamos o res dentro do try, podemos apagá-lo depois do catch.

Salvamos e, para conseguirmos testar, acessaremos nosso navegador e atualizaremos a página. Com isso, a página da API exibe:

{
"status": "Notificacao enviada com sucesso!"
}

Parece estar funcionando, mas para termos certeza, voltaremos para o código do React Native. No Terminal, recebemos um LOG com a mensagem que escrevemos na API, contendo o "score: 850" e o "time: 2:45".

Então o código da mensagem funcionou muito bem e conseguimos criar uma API funcionando. Porém precisamos melhorá-la, porque ainda precisamos atualizar a página da API no navegador.

Seria interessante que, ao criarmos uma nova postagem, ele obtivesse as informações de título, imagem e texto da postagem e enviasse esses dados como notificação, que seria exibida de alguma forma no dispositivo. Integraremos essa parte no próximo vídeo.

@@07
Disparando notificações ao criar post

Até o momento conseguimos construir uma API para simular o envio de uma notificação. Testamos isso acessando um navegador Web com o endereço "localhost:3000/api/spaceapp". Isso nos retornou um JSON com o status "Notificação enviada com sucesso”. Essa notificação realmente foi enviada, como observamos no Terminal da aplicação Mobile.
Contudo, o ideal seria que agora disparássemos essas notificações assim que utilizássemos nossa aplicação web quando criássemos uma nova postagem sobre algo do universo, e é isso que faremos. Então, acessando o código da aplicação Web, precisaremos fazer algumas alterações.

Antes de modificarmos nossa API, criaremos uma função responsável por chamar nossa API e disparar as notificações para todos os aplicativos que têm o SpaceApp instalado. Para isso, acessaremos "src > servicos > firestore.js", que é o arquivo com todas as funções relacionadas ao banco de dados do Firestore.

O ideal é que na função salvarPost(), da linha 4, assim que criássemos uma nova postagem, disparássemos as notificações para os dispositivos. É isso que faremos, mas para criar uma boa prática iremos encapsular a função de enviar notificação, assim é possível reutilizá-la em outras partes da aplicação e até em outras aplicações.

Então dentro da pasta "servicos" criaremos um arquivo chamado "notificacao.js". Esse arquivo conterá todas as funções que criarmos relacionadas à notificação. A primeira delas é a enviarNotificacao.

export async function enviarNotificacao(title, body, image){
  const dados = {
    title,
    body,
    image
  }COPIAR CÓDIGO
Então criamos a enviarNotificacao que recebe como parâmetro três propriedades: o título (title), o corpo (body) e a imagem (image). O título é o que queremos mostrar na notificação, o corpo é a descrição e a imagem é a mesma da publicação.

Feito isso, criamos um objeto chamado dados contendo essas três informações. Com isso, podemos enviar esse objeto para nossa API, onde poderemos disparar a notificação com essas informações.

Para chamar a API, usaremos o fetch. Poderia ser o axios, que utilizamos no curso React Native: utilizando Web API, mas precisaríamos instalar a biblioteca. Então usaremos de fetch que é nativo e, portanto, não precisaremos instalar mais nada na aplicação.

  const resultado = await fetch('/api/spaceapp', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json'
    },
    body: JSON.stringify(dados)
  })
}COPIAR CÓDIGO
Portanto criamos uma const resultado contendo o fetch() com o local para acessar a API entre os parâmetros. Não precisamos usar o "localhost:3000" no endereço porque estamos utilizando o Next nessa aplicação Web, que automaticamente sabe o que deve ser colocado antes do endereço.

Feito isso, passamos chaves ({}) e, dentro delas, alguns atributos. O primeiro foi o método (method) que será utilizado, no caso, será o POST, já que enviaremos dados para disparar a notificação.

Em seguida definimos o headers (cabeçalhos), para informar que estamos criando uma aplicação que gera um JSON. Por fim, usamos o body (corpo) com os dados, mas não podemos mandar apenas os dados, que são um objeto.

Como estamos fazendo uma chamada da API, precisamos passar os dados como se fosse uma string, e para isso convertemos nosso objeto em string usando o JSON.stringify(). Assim, quando acessarmos os dados através da Web API, conseguimos acessar os dados do title, do body e do image.

Salvamos esse código e, em seguida, precisamos chamar a enviarNotificacao quando criarmos uma nova aplicação, que é feita no arquivo "firestore.js" na função "salvarPost()". Nessa função, faremos a chamada após o result, ou seja, na linha 7, escrevendo await enviarNotificacao(data.titulo, data.descricao, data.imagemUrl).

export async function salvarPost(data){
  try {
    const result = await addDoc(collection(db, 'posts'), data)
    await enviarNotificacao(data.titulo, data.descricao, data.imagemUrl)
    return result.id
  } catch(error){
    console.log('Erro add post:', error)
    return 'erro'
  }
}COPIAR CÓDIGO
Salvamos essa alteração e, agora que temos a função enviarNotificacao dentro da salvarPost, precisamos fazer algumas pequenas modificações na nossa API. Sendo assim, acessaremos "pages > api > spaceapp.js".

No "spaceapp.js", precisamos primeiramente acessa o title, o body e o image. Acessaremos todos esses dados a partir da variável req, onde temos o body contendo todas as informações. Para isso, no começo da função handler escrevemos const { title, body, image }= req.body.

export default async function handler(req, res){

  const { title, body, image } = req.body

  const mensagem = {
    notification: {
      title: title,
      body: body,
    },
 //código omitidoCOPIAR CÓDIGO
O .body do req vem do fetch no arquivo "notificacao.js". Se repararmos com atenção na enviarNotificacao, na linha 13, dentro do fetch() de resultado, temos o body com o JSON.stringify(dados). Além disso, depois do resultado, podemos escrever um console.log(resultado) para descobrirmos se tudo correu conforme o esperado.

//código omitido

  const resultado = await fetch('/api/spaceapp', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json'
    },
    body: JSON.stringify(dados)
  })
  console.log(resultado)
}COPIAR CÓDIGO
Vamos salvar a função enviarNotificacao e voltar para o "spaceapp.js", onde precisamos fazer algumas pequenas alterações. A primeira delas é como estamos enviando os dados da notificação, que é como data Dessa forma, mesmo passando várias informações, não teríamos um ícone mostrando a notificação na nossa aplicação.

Abrindo nosso emulador, na parte superior do aparelho temos a status bar (barra de status). Se clicarmos no topo da tela e arrastarmos para baixo, notaremos que todos os aparelhos Android têm uma área dedicada às notificações.

Para as notificações aparecerem, temos que modificar na API para os dados serem do tipo notification. Dentro dessa notificação teremos acesso ao title e ao `body´.

  const mensagem = {
    notification: {
      title: title,
      body: body,
    },
    token: 'fymAfwTZRMyfanSMZ_hRPx:APA91bGfQi_x-VFhAOO0Ly8BjJznceBpmCZUg7a65d3-iDTY8PDUfjlumpU6jV_gAZH50VrLxGWG-DN__1sbT-O5vH3F56SuroWPVsZW73M3rb4M94WOvePQq0arqKdc9AbQLnDgNWwN'
  };
//código omitidoCOPIAR CÓDIGO
Com acesso às duas propriedades no notification, precisamos modificar o token. Percebam que estamos passando uma única string, então apenas um dispositivo receberá essa notificação. O ideal seria que vários dispositivos pudessem receber essa notificação, e para isso modificaremos para tokens e escreveremos em uma array, ou seja, entre colchetes ([]).

  const mensagem = {
    notification: {
      title: title,
      body: body,
    },
    tokens: ['fymAfwTZRMyfanSMZ_hRPx:APA91bGfQi_x-VFhAOO0Ly8BjJznceBpmCZUg7a65d3-iDTY8PDUfjlumpU6jV_gAZH50VrLxGWG-DN__1sbT-O5vH3F56SuroWPVsZW73M3rb4M94WOvePQq0arqKdc9AbQLnDgNWwN']
  };COPIAR CÓDIGO
Agora, se quisermos adicionar novos dispositivos para receberem a notificação, basta escrever uma vírgula depois da string e, dentro dos colchetes, escrever outra string contendo um token. Nós permaneceremos com um, apesar de, com essa forma, podemos adicionar mais de um dispositivo.

Por fim, mudaremos o método .send(), na linha 15, para . sendMulticast(), então fica admin.messaging().sendMulticast(mensagem). Com esse novo método, conseguimos disparar para todos os dispositivos que temos acesso por meio do tokens.

//código omitido

  try {
    await admin.messaging().sendMulticast(mensagem)
    console.log('Notificacao enviada com sucesso!')
    res.status(200).json({
      status: 'Notificacao enviada com sucesso!'
    })
  }

//código omitidoCOPIAR CÓDIGO
Notem que mesmo após essas modificações, ainda não usamos o image, que nós utilizaremos posteriormente. Mesmo assim, para fazermos um teste e descobrir se está funcionando, vamos encerrar nossa aplicação Web no Terminal e depois executaremos novamente, escrevendo npm run dev.

Em seguida, voltaremos ao navegador, atualizaremos a página e, para testarmos se funciona, precisamos criar uma nova postagem. Então clicaremos no botão do canto inferior direito, abrindo uma janela pop-up no centro da tela.

Preencheremos o título como "Lua 2", a fonte como "Hubble", a descrição como "Nova lua" e no link da imagem vamos colar a URL da imagem de Lua. Clicamos no botão salvar no centro inferior da janela. Com isso a postagem é criada tanto na aplicação Web, quanto na aplicação Mobile.

Em seguida, acessaremos o código da aplicação Mobile e observaremos o Terminal. Nele encontramos a notificação disparada foi exibida, então temos os dados de "body" como "Nova Lua". e o "title" escrito "Lua 2". Dessa forma, o envio da notificação realmente funcionou.

Com isso, nossa aplicação Web se comunica com nossa API diretamente. Antes tínhamos feito o acesso da API através de uma URL no navegador, agora quando criamos uma nova postagem é disparada uma notificação.

Ainda precisamos modificar algumas coisas. Lembrem-se que na nossa aplicação Web e na nossa API, armazenamos os tokens diretamente no nosso código. O ideal é acessarmos esses tokens de forma dinâmica, ou seja, conforme novos aparelhos forem utilizando nosso aplicativo conseguíssemos alterar o tokens.

Aprenderemos a fazer essa alteração nos próximos vídeos.

@@08
Faça como eu fiz: projeto web

Ao longo da aula, vimos que o projeto Web será muito importante para disparar as notificações que serão exibidas no celular. Então bora praticar um pouco?
Baixe o projeto Web nesse link ou veja nesse commit do github;
Instale as dependências com npm install;
Configure o projeto Web para utilizar o Firebase Cloud Messaging (FCM), adicionando suas credenciais de projeto no arquivo firebase.js;
Teste a aplicação e verifique se ela carrega tudo referente ao seu Firestore.
Se o projeto Web estiver funcionando corretamente e as informações salvas no Firestore estão sendo carregadas e exibidas nele, agora é preciso configurar o envio de notificações, configurando um servidor para executar essa funcionalidade. Para isso:

Construa a API, conforme abordado em aula;
Adicione os tokens dos dispositivos na API e faça um teste enviando as notificações.

https://github.com/alura-cursos/spaceapp-web/archive/4cd7dd2c7c659f977d77ed2a99d0afe1b121461c.zip

https://github.com/alura-cursos/spaceapp-web/tree/4cd7dd2c7c659f977d77ed2a99d0afe1b121461c

O código da API a ser criada é:
import { admin } from "../../config/firebaseAdmin";

export default async function handler(req, res) {
  async function sendNotification() {

    const { title, body, image } = req.body;

    const message = {
      notification: {
        title: title,
        body: body
      },
      tokens: [
        'ePi6HTkGT5GIEvmpnG6G3M:APA91bGEgzGLmhuKwHQkKzEsiCHsTR__NaS3LTxqTiofJ5gsKqkgwEIF-7dg4UpXQd3krPo6wSFju8lJdxyL8VNelg6A7nnRplBjGiOBleRhmNFdqD6_CUBURHsm1PpuH3an-YzQ5IFH',
        'e57ipf2qR-elET9pWjwExs:APA91bEeniDv4BzZ4d6sHjjQ4AGSceE0rpSmqCNgwJY0HUUK8Tf5cuElVEekEfM_7ZofAyKa7NH-nmanBiOIkDF8F3zbjTGKxi1KH9EDetM-LlAAnVTCQxwxq4P-3Zr08FLvmm_i2-O5'
      ]
    };

    try {
      await admin.messaging().sendMulticast(message);
      console.log('Notification sent successfully');
      return 'Notification sent successfully';
    } catch (error) {
      console.log('Error sending notification: ', error);
      return 'Error sending notification: ', error;
    }
  }

  const result = await sendNotification()

  res.status(200).json({ result });
}COPIAR CÓDIGO
Confira o repositório do projeto completo nesse repositório.

@@09
Sobre Firebase Cloud Messaging na Web

O Firebase Cloud Messaging (FCM) é uma plataforma de mensagens para dispositivos móveis que permite enviar notificações para aplicativos Android, iOS e da Web. A comunicação entre uma aplicação web e o servidor do FCM permite que a aplicação envie e receba mensagens de notificação para o servidor do FCM.
Com base nisso e no que abordamos em aula, marque a alternativa que explica como uma aplicação web pode se comunicar com o servidor do FCM?

Através de uma API, a aplicação web pode se comunicar com o servidor do FCM e enviar notificações push para dispositivos móveis registrados.
 
A criação de uma API é um forma que permite à aplicação se comunicar com o servidor do FCM e enviar notificações push. Com a API, tanto a aplicação Web quanto a aplicação Mobile conseguem interagir com o FCM de forma indireta.
Alternativa correta
O login com o Google é uma das formas de autenticar uma aplicação Web para envio de notificações por meio do FCM.
 
Alternativa correta
A Aplicação Web pode enviar notificações para os dispositivos móveis de forma direta, sem precisar de serviço intermediário.
 
Alternativa correta
Para se comunicar com o FCM a aplicação Web precisa de uma e-mail autorizado pelo Firebase para permitir que funcione.

@@10
O que aprendemos?

A segunda aula foi finalizada, show!!! E nela você aprendeu que para conseguir enviar uma notificação push é preciso de ter um serviço intermediário e com isso criamos uma API. E para usar essa API nós integramos ela em uma aplicação Web.
Nessa aula, você aprendeu como:

Enviar notificações para o Android pelo console do Firebase;
Baixar e configurar um projeto Web feito com Next.js;
Criar uma API para enviar as notificações;
Disparar notificações quando um post é criado na Web;
Mais uma aula finalizada. #Partiu aula 3?

Vamos lá!

#### 29/01/2024

@03-Armazenando tokens na web

@@01
Projeto da aula anterior

Você pode revisar o seu código e acompanhar o passo a passo do desenvolvimento do nosso projeto e, caso deseje, você pode baixar o projeto MOBILE da aula anterior e o baixar o projeto WEB.
Bons estudos!

https://github.com/alura-cursos/react-native-firebase-notification/tree/aula2

https://github.com/alura-cursos/spaceapp-web/tree/914d80cbb2c199423be28cb80d2d857146cd8822

@@02
Armazenando tokens no Firestore

Conseguimos construir nossa API utilizando uma aplicação web feita com o Next afim de disparar notificações para o nosso dispositivo. Contudo, a API que construímos armazena o token diretamente no código.
Esta configuração é válida para testes iniciais, pois nos permite visualizar se a notificação funciona. Entretanto, na prática, não é o ideal, pois cada vez que uma nova pessoa utiliza nosso aplicativo, teremos que acessar o código da API e adicionar manualmente o token do novo dispositivo e tornar possível o envio de notificações a ele.

O ideal é que este processo seja automático. Existem diversas maneiras de realizar essa automatização, entre as quais destacamos duas:

Criar uma variável para que nossa API armazene os tokens toda vez que um aparelho for registrado.
Salvar diretamente em um banco de dados.
Já que estamos utilizando neste curso diversos serviços do Firebase, criaremos nele uma nova coleção para armazenar o token quando o dispositivo for inicializado.

Para isso, voltaremos ao navegador e acessaremos o nosso Firestore por meio do console do Firebase. Em seu interior, veremos que ele possui somente uma coleção, denominada "posts", a qual possui todos os dados dos posts que foram cadastrados e publicados.

Criaremos uma nova coleção para armazenar os tokens. Existem diversas maneiras de armazená-los — uma delas consiste na criação de um arranjo com as strings de todos os tokens.

É importante saber que o *token não é 100% fixo e único*. Vamos abrir o terminal e visualizar o token do nosso dispositivo, que inicia com os caracteres "feT1".

Suponhamos que a pessoa usuária limpou a memória do aplicativo no seu dispositivo, realizando em seguida um novo login. Abriremos lado a lado o nosso terminal e o nosso emulador Android. Por meio deles, seguiremos os seguintes passos, simulando a ação da pessoa usuária:

Acessaremos nossa aplicação por meio do emulador Android.
Limparemos toda a memória de armazenamento do aplicativo.
Logaremos novamente na aplicação.
Neste momento, precisaremos autenticar novamente, digitando o e-mail e a senha. Visualizaremos o terminal e perceberemos que, quando entramos na aplicação, o token foi modificado — agora ele inicia com os caracteres "f_z2".

Temos que identificar cada pessoa usuária com um token. Para isso, criaremos um objeto que conterá um id único para cada uma delas.

Como conseguiremos este id? Por meio da autenticação de login que realizamos na tela inicial da aplicação. Identificaremos cada pessoa usuária específica pelo id único do login e adicionaremos o token como outro atributo, tornando possível o envio de notificações.

O id e o token são atributos diferentes, mas serão utilizados ao mesmo tempo para enviar notificações personalizadas.

Criando
Por meio do explorador, acessaremos o arquivo firestore.js por meio do caminho "src > servicos". Nele, criaremos uma nova função para salvar um token que será muito similar à salvarPost(). Copiaremos o código desta última e colaremos abaixo dela mesma.

Alteraremos o nome da função colada para salvarToken() e faremos as alterações abaixo.

Dentro do try, ao invés de salvar collection('posts'), salvaremos collection('tokens').
Dentro do catch, alteraremos o erro do console.log() de 'Erro add post:' para 'Erro ao adicionar token:'.
export async function salvarPost(data){

    //Código omitido

}

export async function salvarToken(data){
    try {
        const result = await firestore().collection('tokens').add(data)
        return result.id
    } catch(error){
        console.log('Erro ao adicionar token:', error)
        return 'erro'
    }
}COPIAR CÓDIGO
Vamos chamar a nova função em algum lugar. Normalmente a chamamos quando o dispositivo inicia, portanto , vamos chamá-la no interior da função que exibe o token do dispositivo no nosso console. Contudo, esta função se encontra no código principal, ou seja, no index.js da pasta "Principal", dentro do bloco useEffect().

Acessaremos este arquivo pelo caminho "src > telas > Principal".

useEffect(() => {
    pegarPostsTempoReal(setPosts);

    requestUserPermission();

    pegarToken()

    messaging().oonMessage( async mensagem => {
        console.log(mensagem)
    })
}, [])COPIAR CÓDIGO
Neste arquivo, acessaremos o interior das chaves da async function pegarToken() que fica acima do useEffect(). Nela, logo abaixo da função getToken(), adicionaremos um await salvarToken() seguido de um bloco de chaves. Dentro deste, adicionaremos duas informações.

ID da pessoa usuária, por meio de um userId que será inicializado com uma string vazia.
Token da pessoa usuária, por meio de um token que será inicializado com a constante token na qual armazenamos o token por meio de um getToken().
async function pegarToken(){
    const token = await messaging().getToken()
    await salvarToken({
        userId: '',
        token:
    })
    console.log(token)
}

useEffect(() => {

    //Código omitido

})COPIAR CÓDIGO
Se tudo der certo, teremos o salvamento no nosso Firebase.

Recolheremos o id da pessoa usuária utilizando o auth. Vamos importá-lo de config/firebase adicionando o comando abaixo como último item na lista de imports. deste arquivo

import { auth } from "../../config/firebase";COPIAR CÓDIGO
Para recolher este id, entre o getToken() e o salvarToken() adicionaremos uma const userId que será igual a auth.currentUser.uid.

async function pegarToken(){
    const token = await messaging().getToken()
    const userId = auth.currentUser.uid
    await salvarToken({
        userId: '',
        token:
    })
    console.log(token)
}

useEffect(() => {

    //Código omitido

})COPIAR CÓDIGO
Salvaremos o código e veremos que nada de novo acontece no emulador. Contudo, se acessarmos o console do firebase pelo navegador e atualizarmos a página, será exibida uma nova coleção denominada "tokens". Dentro dela temos tanto o token quanto o id único da pessoa usuária.

Desta forma, podemos armazenar vários tokens, e se quisermos enviar uma mensagem específica para determinado dispositivo, podemos buscar pelo id e disparar a mensagem para o token salvo.

A seguir faremos este processo, integrando-o na nossa API da web. Até lá.

@@03
Faça como eu fiz: token do dispositivo

Vamos praticar o que aprendemos em aula!
Uma vez que o Firestore já está configurado no projeto mobile, é possível pegar o token relacionado ao dispositivo, por meio das funções disponíveis da biblioteca do Cloud Messaging. Podemos pegar esse token em dois momentos, quando o aplicativo é carregado pela primeira vez ou quando o usuário faz login no aplicativo.

Para que possa praticar, crie uma função no arquivo firestore.js para salvar o token no Firestore. Dessa forma é possível recuperar eles para disparar as notificações para os usuários.

O token é uma identificação única do dispositivo, gerada pelo FCM (Firebase Cloud Messaging) e nos permite enviar notificações direcionadas a um dispositivo específico. Armazenando esses tokens no Firestore, é possível enviar mensagens personalizadas a dispositivos selecionados. O código ficará dessa forma:
export async function salvarToken(data){
  try {
    const result = await firestore().collection('tokens').add(data)
    return result.id
  } catch(error){
    console.log('Erro ao adicionar token:', error)
    return 'erro'
  }
}COPIAR CÓDIGO
Você pode conferir o código desta atividade a partir deste commits.

https://github.com/alura-cursos/react-native-firebase-notification/tree/a2b933bf9d8c58dd638284e4006673842ee55bc7

@@04
Enviando notificações para tokens salvos

Já temos os tokens armazenados no Firestore e conseguimos identificar a qual dispositivo ele pertence, para assim enviar notificações. Para isso, utilizamos o próprio id que recebemos com o login.
Se abrirmos e observarmos o código da API que pertence à aplicação web (arquivo spaceapp.js), veremos que o armazenamento dos tokens é feito diretamente no código da API. Este processo não é ideal.

Podemos acessar o spaceapp.js por meio do explorador, através do caminho "src > pages > api".
Agora que temos tudo armazenado no Firestore, consumiremos estes dados e enviaremos as notificações a partir do token disponível neste local, tornando o processo mais dinâmico e automático, eliminando a necessidade de adicionar um novo token sempre que uma nova pessoa usuária utilizar nossa aplicação.

Para isso, poderíamos acessar o arquivo spaceapp.js do nosso aplicativo web, onde seria feito o consumo do dado no Firestore. Alternativamente, podemos aproveitar que existe um arquivo chamado firestore.js na aplicação web. Este arquivo dedica-se a funções que consomem dados do Firestore.

Podemos acessar o arquivo firestore.js por meio do explorador, através do caminho "src > servicos".
Em seu interior, criaremos uma função para retornar uma lista de tokens, similar ao que fizemos anteriormente, quando consumimos outros dados do Firestore. Abaixo da função salvarPost() criaremos a função async function pegarTokens(), exportando-a adicionando um export à sua esquerda.

No interior do bloco de chaves desta função, adicionaremos um bloco try e catch(). Neste último, passaremos entre parênteses o error e entre chaves um console.log(error) para exibir o erro no terminal.

Entre as chaves do try recuperaremos as informações dos tokens salvos no Firestore. Para isso, criaremos a const tokensRef que será uma referência para os tokens. Ela será igualada ao query() que receberá entre seus parênteses a nossa collection(db, "tokens"), onde db recupera o banco de dados e "tokens" informa qual coleção queremos.

export async function salvarPost(data){

Código omitido

}

export async function pegarTokens(){
  try {
        const tokensRef = query(collection(db, "tokens"))
    } catch(error){
        console.log(error)
    }
}COPIAR CÓDIGO
Agora que temos nossa referência, recolheremos as informações seguindo a recomendação da documentação e adicionando no try uma const querySnapshot que será igual a getDocs(). Este precisará esperar a chegada da informação, portanto adicionaremos um async à sua esquerda. Dentro de seus parênteses, passaremos a nossa tokensRef.

export async function pegarTokens(){
  try {
    const tokensRef = query(collection(db, "tokens"))
    const querySnapshot = await getDocs(tokensRef)
    }
  catch(error){
    console.log(error)
  }
}COPIAR CÓDIGO
Desta forma, um snapshot (captura rápida) das informações será feito e armazenado na nossa variável, o que nos dará acesso aos tokens salvos.

Se verificarmos o Firestore, ele retornará um objeto constituído do id e do token do dispositivo. Contudo, queremos apenas os tokens na lista, por isso faremos um filtro que retornará apenas as strings deles. Para isso, abaixo da const querySnapshot criaremos a variável tokens, que receberá inicialmente um arranjo vazio.

A partir do querySnapshot, percorreremos e filtraremos todos os elementos obtidos pelo arranjo, para retornar somente os tokens. Para isso, abaixo da const tokens adicionaremos um querySnapshot.forEach().

Este forEach chamará cada objeto recolhido de "documento", assim como no Firestore — para isso, adicionaremos entre seus parênteses um doc envolvido pelos parênteses de uma função seta () => {}. Entre as chaves desta, recolheremos o tokens.push(), adicionando entre parênteses somente o doc.data().token.

export async function pegarTokens(){
  try {
    const tokensRef = query(collection(db, "tokens"))
    const querySnapshot = await getDocs(tokensRef)
    const tokens = []
    querySnapshot.forEach((doc) => {
      tokens.push(doc.data().token)
    })
  }
  catch(error){
    console.log(error)
  }
}COPIAR CÓDIGO
Acessando o Firestore por meio do navegador, verificaremos que estamos salvando esta informação como token. Ele tentará acessá-la no console do Firebase e retornar apenas a string do token.

Voltaremos ao arquivo firestore.js do aplicativo web, no qual finalizaremos o bloco try com um return tokens. Qualquer parte do código que chamar esta função, selecionará no banco de dados e retornará uma lista com os tokens.

export async function pegarTokens(){
  try {
    const tokensRef = query(collection(db, "tokens"))
    const querySnapshot = await getDocs(tokensRef)
    const tokens = []
    querySnapshot.forEach((doc) => {
      tokens.push(doc.data().token)
    })
    return tokens
  }
  catch(error){
    console.log(error)
  }
}COPIAR CÓDIGO
Para testar, abriremos o arquivo spaceapp.js. Em seu interior, abaixo de const { title, body, image }, criaremos a variável const tokens que será igual a await pegarTokens().

export default async function handler(req, res){
    const { title, body, image } = req.body

    const tokens = await pegarTokens()

//Código omitido

}COPIAR CÓDIGO
Ao digitar "pegarTokens" e pressionar "Enter", o sistema fará a importação automática da função, adicionando o código abaixo no final da lista de imports.

import { pegarTokens } from '../../servicos/firestore';COPIAR CÓDIGO
Já que temos acesso aos nossos tokens, vamos adicionar um console.log(tokens) para imprimir no terminal e verificar se está funcionando conforme o esperado.

export default async function handler(req, res){
    const { title, body, image } = req.body

    const tokens = await pegarTokens()
    console.log(tokens)

//Código omitido

}COPIAR CÓDIGO
Vamos apagar a string no interior do vetor tokens, já que o retorno do console.log(tokens) será um vetor de tokens.

export default async function handler(req, res){

//Código omitido

  const mensagem = {

// Código omitido

    tokens: ['fymAfwTZRMyfanSMZ_hRPx:APA91bGfQi_x-VFhAOO0Ly8BjJznceBpmCZUg7a65d3-iDTY8PDUfjlumpU6jV_gAZH50VrLxGWG-DN__1sbT-O5vH3F56SuroWPVsZW73M3rb4M94WOvePQq0arqKdc9AbQLnDgNWwN']
  };

//Código omitido

}COPIAR CÓDIGO
Em seu lugar, adicionaremos um tokens que contém o vetor (ou seja, uma lista) de tokens.

export default async function handler(req, res){

//Código omitido

  const mensagem = {

// Código omitido

    tokens: tokens
  };

//Código omitido

}COPIAR CÓDIGO
Salvaremos o código e acessaremos a aplicação web no navegador para ver se funciona. Utilizaremos o endereço abaixo.

localhost:3000
Para testar, criaremos uma nova postagem. Copiaremos o endereço de uma das imagens na tela e clicaremos no botão "+" no canto inferior direito.

A tela de novo post será aberta, onde preencheremos os campos conforme abaixo:

no Título, digitaremos "Teste"
no Link da imagem, colaremos o link da imagem copiada
Os outros campos serão deixados em branco. Clicaremos em "Salvar" e veremos o novo post criado na tela. Voltaremos ao código e veremos o que aconteceu.

No terminal, será exibido o vetor que possui o único token salvo no Firestore e logo abaixo dele a mensagem abaixo.

Notificacao enviada com sucesso!
Isso significa que conseguimos acessar o banco de dados, recuperar os tokens e enviar uma mensagem. Toda vez que um novo token for registrado, a nossa lista será atualizada dinamicamente.

Vamos conferir em nosso dispositivo se a mensagem chegou. Para isso, minimizaremos o código da aplicação web e acessaremos o código da aplicação mobile, cujo terminal exibirá a mensagem recebida. Ela possui um "title": "Teste" e não possui nenhum body, por isso nenhum corpo é exibido na mensagem.

LOG {"collapseKey": "com.spaceapp", "data": {}, "from": "369507489110", messageId": "0:1674220477365003%aa773528aa773528", "notification": {"android": {}, "title": "Teste"}, "sentTime": "1674220477356", "ttl": 2419200}
Neste vídeo recuperamos as informações no Firestore. Contudo, se observarmos o nosso código Mobile que salva essas informações — ou seja, a função salvarToken() — veremos que existe um detalhe que poderá causar problemas no futuro: não verificamos se o *token já existe e já está salvo no Firestore*.

Se reiniciarmos a aplicação, veremos que a função salvarToken() será chamada novamente. Já sabemos que ela será chamada toda vez que a aplicação iniciar.

Acessaremos o banco de dados do Firebase por meio do navegador e veremos que existem dois *tokens salvos que são exatamente iguais*.

Queremos evitar redundâncias como esta para evitar consumir excessivamente o banco de dados.

A seguir, faremos a correção deste problema.

@@05
Faça como eu fiz: recuperar tokens

Vamos praticar!
Com os tokens salvos no Firestore, é possível obtê-los no servidor web que foi criado para enviar as notificações. Isso pode ser feito utilizando as APIs do Firestore para recuperar os tokens, de acordo com os critérios específicos que são necessários para enviar as notificações. Para isso, faça o seguinte:

Crie uma função no arquivo firestore.js que busque os tokens salvos;
Desenvolva a função que busque todos os tokens armazenados e os retorne como um array de strings.

Criamos uma função para recuperar os tokens de forma automática. Dessa forma, sempre que um novo dispositivo entrar na aplicação, ele receberá notificações sem a necessidade de adição manual. Então você irá conseguir enviar notificações para todos os dispositivos de forma automática e segura. O código da função ficará assim:
export async function pegarTokens(){
  try {
    const ref = query(collection(db, "tokens"))
    const querySnapshot = await getDocs(ref)
    const tokens = []
    querySnapshot.forEach(( doc ) => {
      tokens.push(doc.data().token)
    })
    return tokens
  }
  catch(error){
    console.log(error)
    return 'error'
  }
}COPIAR CÓDIGO
A função pegarTokens tem como objetivo recuperar tokens do banco de dados. Para isso, ela inicializa o Firestore com a biblioteca do Firebase e acessa a collection "tokens". Em seguida, utiliza o método forEach para percorrer cada documento na collection e adicionar cada token a uma lista de tokens. E depois, essa lista será retornada.

Você pode conferir o código desta atividade a partir deste commit.

https://github.com/alura-cursos/spaceapp-web/tree/85c813bb2e82f1d80622a7ad1994c5381418ba6e

@@06
Lidando com duplicações de tokens

Percebemos através do console do Firebase que, a cada reinicialização da aplicação, um novo documento é criado dentro da coleção "tokens" com as mesmas informações de userId e de token.
Este processo não é o ideal, pois toda vez que alguém abrir o aplicativo, ele registrará no nosso Firestore. O ideal é realizar verificações antes do registro.

Podemos verificar se esta pessoa usuária já está salva no "tokens" ou atualizar o token. Anteriormente, vimos que se desinstalamos ou limpamos o aplicativo, um novo token seria gerado. Portanto, mesmo se tratando do mesmo dispositivo, o token muda.

Precisamos atualizar a informação específica de cada pessoa usuária no campo token. Para isso, alteraremos o código que salva o token no Firestore.

Voltaremos ao código da aplicação Mobile, no arquivo firestore.js. Antes de salvar qualquer informação por meio da função salvarToken(), precisaremos verificar se o *token já existe e atualizá-lo caso ele exista*.

Para isso, dentro de salvarToken(), na primeira linha do bloco try, acima da const result, adicionaremos uma const tokens para recolher todos os tokens salvos no Firestore. Ela receberá um await firestore().collection('tokens') que recolhe os documentos da coleção "tokens".

export async function salvarToken(data){
    try {
        const tokens = await firestore().collection('tokens')
        const result = await firestore().collection('tokens').add(data)
        return result.id
    } catch(error){
        console.log('Erro ao adicionar token:', error)
        return 'erro'
    }
}COPIAR CÓDIGO
Poderíamos utilizar um get para recolher tudo, mas esse procedimento não é o ideal nesse momento. Em vez disso, aplicaremos filtros oferecidos pelo próprio Firebase. Dessa forma, ao invés de armazenar todos os tokens dentro da variável tokens, armazenaremos apenas o token existente.

À direita de collection('tokens'), adicionaremos o filtro .where() que receberá entre parênteses o comando 'userId', '==', data.userId para verificar se o campo userId é igual ao data.userId.

Se ele encontrar, faremos um .get(), adicionando-o à direita do where().

export async function salvarToken(data){
    try {
        const tokens = await firestore().collection('tokens').where('userId', '==', data.userId).get()
        const result = await firestore().collection('tokens').add(data)
        return result.id
    } catch(error){
        console.log('Erro ao adicionar token:', error)
        return 'erro'
    }
}COPIAR CÓDIGO
Vamos entender o código? Ele diz que vamos acessar o Firestore, na coleção "tokens", onde recolheremos o token somente no caso em que o id da pessoa usuária for igual ao id do dispositivo acionado. Neste caso, ele retornará essa informação e a salvará na variável tokens.

Com isso em mente, abaixo da const tokens faremos um if conforme abaixo.

if(tokens.docs.length > 0){
    await firestore().collection('tokens').doc(tokens.docs[0].id)
}COPIAR CÓDIGO
Esta condicional verifica se tokens.docs.length é maior que 0 — ou seja, se há algo dentro dos documentos da variável tokens. Se houver, significa que encontramos uma pessoa usuária que possui o userId. A partir disso, atualizaremos o token.

Entre os parênteses de doc() especificamos qual documento queremos atualizar. Como já o temos salvo na variável tokens, podemos recolher o primeiro documento escrevendo tokens.docs[0].

Retornaremos somente a primeira posição da lista, pois o ideal é que haja somente uma informação correspondente à nossa busca. Já o id corresponde ao id do documento.

Com o id em mãos, adicionamos o .update() para atualizar a informação, informando entre seus parênteses o data. O próprio Firebase lida com a verificação de qual campo será modificado e se a atualização é realmente necessária. Caso haja uma alteração no token do dispositivo por qualquer motivo, o Firebase fará essa atualização.

export async function salvarToken(data){
    try {
        const tokens = await firestore().collection('tokens').where('userId', '==', data.userId).get()
        if(tokens.docs.length > 0){
            await firestore().collection('tokens').doc(tokens.docs[0].id).update(data)
        }
        const result = await firestore().collection('tokens').add(data)
        return result.id
    } catch(error){
        console.log('Erro ao adicionar token:', error)
        return 'erro'
    }
}COPIAR CÓDIGO
Existem vários motivos pelos quais um token pode ser alterado no dispositivo. Vimos que um deles é a atualização do cache. Além disso, é possível que a Google trabalhe em atualizações que também modifiquem estes tokens.

Apesar de não ser possível controlarmos estas mudanças, podemos amenizar os problemas com o envio de notificações através do update(), garantindo que o dispositivo as receba.

Dentro do bloco if, abaixo da nossa lógica, retornaremos o id do primeiro documento da lista por meio de um return tokens.docs[0].id.

if(tokens.docs.length > 0){
    await firestore().collection('tokens').doc(tokens.docs[0].id)
    return tokens.docs[0].id
}COPIAR CÓDIGO
Desta forma, ele não salvará nem criará um token. Caso o if retorne que o tamanho do arranjo é igual a, significa que ele está vazio e não haverá nada a atualizar. Neste caso, será criado um novo dispositivo.

Abaixo temos o código completo da função.

export async function salvarToken(data){
    try {
        const tokens = await firestore().collection('tokens').where('userId', '==', data.userId).get()
        if(tokens.docs.length > 0){
            await firestore().collection('tokens').doc(tokens.docs[0].id).update(data)
            return tokens.docs[0].id
        }
        const result = await firestore().collection('tokens').add(data)
        return result.id
    } catch(error){
        console.log('Erro ao adicionar token:', error)
        return 'erro'
    }
}COPIAR CÓDIGO
Salvaremos o código. Para testá-lo, acessaremos o console do Firebase no navegador e excluiremos todas as informações sobre tokens. Para isso, seguiremos os passos abaixo:

na coluna à esquerda, clicaremos na coleção "tokens";
na coluna central, clicaremos no token a ser excluído;
na coluna à direita, clicaremos no botão com três pontos na vertical e selecionaremos "Excluir documento".
na caixa de mensagem que será aberta, selecionaremos o botão "Começar a exclusão".
Faremos o mesmo procedimento para o outro token da coleção. Desta forma, a coleção "tokens" ficará vazia.

Voltaremos ao código da aplicação web e reiniciaremos a aplicação. No emulador, seremos logados automaticamente. Se voltarmos ao console do Firebase e olharmos a coleção, um novo token aparecerá para o nosso dispositivo, assim como esperado.

Voltando ao código e ao emulador, reiniciaremos novamente a aplicação para verificar se um novo token será criado. Voltando ao console do Firebase, vamos atualizá-lo e assim perceber que não foi gerado um novo documento, confirmando que nosso código funcionou.

Agora precisamos testar no nosso console se, caso modifiquemos o token do nosso dispositivo, o campo token será alterado, sem a criação de um novo. Para isso, memorizaremos os primeiros caracteres do token atual e voltaremos ao código da aplicação web.

Acessaremos o emulador, onde fecharemos a aplicação e limparemos novamente o cache e o armazenamento. Fecharemos todas as abas e inicializaremos nossa aplicação pelo terminal.

Nesse momento, precisaremos autorizar tudo e logar novamente com nosso e-mail e senha. Ao entrarmos na aplicação, veremos no terminal que um novo token foi gerado, com iniciais diferentes.

Voltando ao console do Firebase, veremos que o campo token foi atualizado conforme o esperado, substituindo o token antigo pelo novo, sem gerar outro documento.

Caso ocorra algo no Firebase que modifique o token de mensagem, teremos o campo atualizado na nossa coleção de tokens.

Nossa aplicação está mais segura em relação a estes dados e não consumiremos de maneira excessiva o armazenamento do Firestore. Por meio da nossa API, conseguimos pegar as informações do token através da nossa aplicação web e disparar e-mails para todos os dispositivos cadastrados.

Feito isso, falta exibir as notificações no nosso dispositivo. Estamos realizando tudo no console, o que já é interessante. Contudo, precisamos mostrar visualmente essas informações.

A seguir, modificaremos o ícone de sino para exibir uma contagem de notificações recebidas e exibiremos as notificações na página de notificações que será acessada através de um clique neste sino.

Aplicaremos também um novo conceito: o Background, com o qual nosso dispositivo receberá mensagens mesmo se estiver completamente fechado ou com a tela desligada.

Nos vemos lá!

@@07
Faça como eu fiz: recuperar os tokens

Vamos praticar!
Conforme abordamos na videoaula, é preciso adicionar um certo nível de verificação para evitar que nosso banco de dados salve tokens de forma duplicada. Para isso, sempre que for salvar um token é importante verificar se ele já não está salvo lá, consultando o id do usuário.

Por isso, modifique a sua função salvarToken para fazer essa verificação antes de salvar.

Se tiver alguma dúvida, procure nossa comunidade no Discord para compartilhar e interagir com outras pessoas, ou o fórum do curso.

A modificação da função salvarToken ficará assim:
export async function salvarToken(data){
  try {
    const tokens = await firestore().collection('tokens').where('userId', '==', data.userId).get()
    if(tokens.docs.length > 0){
      await firestore().collection('tokens').doc(tokens.docs[0].id).update(data)
      return tokens.docs[0].id
    }
    const result = await firestore().collection('tokens').add(data)
    return result.id
  } catch(error){
    console.log('Erro ao adicionar token:', error)
    return 'erro'
  }
}COPIAR CÓDIGO
Você pode conferir o código desta atividade a partir deste commits.

https://github.com/alura-cursos/react-native-firebase-notification/tree/b88df40bdb8be6950c936a566cebc3d890e6d9e0

@@08
Sobre os tokens

Durante a aula, aprendemos sobre como utilizar os tokens na nossa aplicação e as funcionalidades que podem ser adicionadas com os mesmos. Considerando o que foi apresentado, marque a alternativa correta:

O token gerado é único por usuário e não se altera ao longo do tempo.
 
O token pode ser alterado por alguns motivos, como quando uma pessoa desinstala e instala novamente o nosso App ou por alguma atualização interna do Firebase. Por isso uma boa prática é sempre atualizar o seu valor no Firestore quando o usuário faz login no App.
Alternativa correta
O token do dispositivo é gerado a partir do e-mail e senha cadastrados no Firebase.
 
O token é uma verificação única por aplicativo e dispositivo, não tendo a necessidade de precisar de um login com e-mail e senha para conseguir gerá-lo.
Alternativa correta
É necessário instalar uma biblioteca adicional para armazenar os tokens do dispositivo na collection do Firestore.
 
Não há a necessidade de instalar uma biblioteca adicional para armazenar os tokens no Firestore, com a própria biblioteca do firebase já é possível fazer isso.
Alternativa correta
Armazenar os tokens do dispositivo na collection do Firestore é uma boa forma de garantir que as notificações enviadas sejam personalizadas para cada dispositivo.
 
Isso aí! Armazenar os tokens no Firestore permite recuperar tokens específicos para enviar notificações personalizadas e a sincronização em tempo real mantém os tokens atualizados mesmo com alterações.
Parabéns, você acertou!

@@09
Desafio: envio de notificações para dispositivos específicos

Chegou a hora do desafio!!!
Nas aulas criamos uma função que pega os tokens de todos os usuários da nossa aplicação do SpaceApp. Mas e se quiséssemos mandar uma notificação para um grupo de usuários específicos? Então é um desafio para você!

Crie uma função na aplicação Web que retorne apenas os tokens referentes a uma lista de IDs dos usuários;
Use essa lista de tokens para enviar as notificações.
Queremos ver o resultado do seu desafio! Compartilhe nas suas redes sociais e marque a gente. Ou se preferir compartilha na nossa comunidade do Discord.

Abaixo tem um exemplo de função que retorna essa lista com base no userId:
export async function pegarTokensPorUserId(userIds){
  try {
    const tokensRef = query(collection(db, "tokens"))
    const querySnapshot = await getDocs(tokensRef)
    const tokens = []
    querySnapshot.forEach((doc) => {
      if(userIds.includes(doc.data().userId)){
        tokens.push(doc.data().token)
      }
    })
    return tokens
  }
  catch(error){
    console.log(error)
  }
}COPIAR CÓDIGO
E para usá-la na nossa API, podemos chamá-la da seguinte maneira:

import { admin } from '../../config/firebaseAdmin';
import { pegarTokens, pegarTokensPorUserId } from '../../servicos/firestore';

export default async function handler(req, res){

  const { title, body, image } = req.body

  const tokens = await pegarTokensPorUserId(['X7Tgmqvn9aPKCSmbF34jNFQEJTH2'])

  const message = {
    android: {
      notification: {
        image: image,
        color: '#0A2E5B',
        title: title,
        body: body
      }
    },
    tokens: tokens
  };

  try {
    await admin.messaging().sendMulticast(message)
    console.log('Notificacao enviada com sucesso!')
    res.status(200).json({
      status: 'Notificacao enviada com sucesso!'
    })
  }
  catch(error){
    console.log(error)
    res.status(400).json({
      status: 'Erro ao enviar'
    })
  }
}COPIAR CÓDIGO
Assim, a nossa API enviaria notificações somente para alguns usuários específicos, no exemplo fornecido seria para apenas um único usuário.

@@10
O que aprendemos?

Parabéns! Você finalizou a terceira aula e nela você aprendeu:
Como utilizar os tokens na sua aplicação;
Desenvolver funções para salvar os tokens e para recuperar os mesmos;
Como utilizar uma aplicação web para enviar as notificações;
Como enviar notificações para dispositivos específicos.