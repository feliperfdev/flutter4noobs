# Flutter SDK

Flutter é um SDK desenvolvido pela Google com a proposta de criar aplicações rápidas e bonitas para mobile, desktop e web a partir de uma única `codebase`. É totalmente gratuída, `open source` e usada por desenvolvedores e empresas do mundo todo.

Se tiver interesse em se aprofundar mais na documentação do Flutter: [flutter.dev](https://flutter.dev/)

## Algumas libs do Flutter

```dart
import 'package:flutter/material.dart';
import 'package:flutter/services.dart';
```

A divisão de import de algum package do Flutter, é organizado no seguinte padrão:

```dart
import 'package:<package>/<library>.dart'
```

## O famoso [pub.dev](https://pub.dev/)

Uma coisa muito comum também para o Flutter é a contribuição que boa parte da comunidade faz para todo o seu ecossistema de packages.

No site [pub.dev](https://pub.dev/) podemos encontrar uma diversidade de packages, tanto para o Dart em si quanto para o Flutter. Packages para tudo: `animações`, `efeitos`, `imagens`, `áudio`, `gerenciamento de estado`, `requisições http`, `gráficos`, `notificações`, `API´s`...

### O pubspec.yaml

O `pubspec.yaml` é um arquivo gerado quando se cria um projeto no Flutter. É onde instalamos as dependências de nossa aplicação, além de podermos configurar os assets e as fontes de texto.

Ou seja, é nesse arquivo onde passamos os packages que queremos instalar em nossas aplicações. Normalmente, a forma de instalar é informada na própria documentação do package.<p>
Exemplo:

```yaml
dependencies:
  http: ^0.12.2
  flutter_modular:
  mobx:
```

Geralmente, ao salvarmos o arquivo `pubspec.yaml`, é rodado automaticamente o comando

```bash
pub get
```

ou

```bash
flutter pub get
```

para usar as dependências.

Depois, basta importar o package na aplicação utilizando o import.
