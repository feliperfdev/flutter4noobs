# Instalação do Flutter no Linux

## Download do SDK do java

Antes de começar a instalar os pacotes do flutter, é importante termos instalado o SDK do Java na máquina, para isso, utilize o comando

```
sudo apt install openjdk-8-jdk
```

Para verificar se a instalação foi bem sucedida e saber a versão do java, rode o comando

```bash
java --version
```

## Download e instalação do Flutter

Para fazer o download do Flutter, acesse o [site oficial](https://flutter.dev/docs/get-started/install/linux) e siga as instruções para instalar o flutter manualmente. A documentação está bem detalhada, mas qualquer dúvida você pode abrir uma [issue](https://github.com/feliper2002/flutter4noobs/issues) e colocar sua dúvida!
<br>
<br>
Para saber se a instalação foi bem sucedida, rode o comando
```bash
flutter doctor
```
Esse comando verifica se a sua máquina tem todos os programas necessários para que você consiga desenvolver com o flutter.

Um dos problemas apontados pelo futter doctor, é a falta das licensas do Android.

Para aceitar as licensas, use o comando

```bash
./Android/sdk/tools/bin/sdkmanager --licenses
```

É recomendado também que você tenha:

- 1 O editor de texto [Visual Studio Code](https://code.visualstudio.com/)
- 2 O [plugin do Flutter](https://marketplace.visualstudio.com/items?itemName=Dart-Code.flutter) para o VSCode
- 3 O [plugin do dart](https://marketplace.visualstudio.com/items?itemName=Dart-Code.dart-code) para o VSCode
- 4 O Emulador de Android [Android Studio](https://developer.android.com/studio)
