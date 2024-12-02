# Como fazer requisições HTTP no Flutter com Dio ✨

Fala, dev! Bora aprender a fazer umas requisições HTTP no Flutter usando o Dio? Essa biblioteca é braba e vai facilitar tua vida na hora de consumir umas APIs. Cola comigo que eu te mostro o passo a passo! 😎

## O que é o Dio? 

O Dio é tipo aquele amigo que resolve tudo: faz requisição GET, POST, PUT, DELETE, tudo com estilo. Olha só o que ele manda:
- Configuração fácil de headers e query params;
- Suporte a timeout (adeus, requisições eternas);
- Cancelamento de requisições (quando você muda de ideia no meio do caminho);
- Intercepta tudo antes e depois das requisições.

## Bora pro código?

### 1. Adiciona o Dio no projeto
Primeiro, abre teu `pubspec.yaml` e joga essa belezinha lá:

```yaml
dependencies:
  dio: ^5.3.2 # Atualiza pra última versão, ein!
```

Depois, manda aquele clássico:

```bash
flutter pub get
```

### 2. Configura o Dio no estilo profissional

Vamos criar uma classe pra deixar tudo organizadinho. É tipo deixar a casa arrumada antes de chamar visita. 

```dart
import 'package:dio/dio.dart';

class DioClient {
  final Dio _dio = Dio(
    BaseOptions(
      baseUrl: 'https://jsonplaceholder.typicode.com',
      connectTimeout: const Duration(seconds: 10),
      receiveTimeout: const Duration(seconds: 10),
    ),
  );

  Dio get dio => _dio;

  DioClient() {
    _dio.interceptors.add(
      InterceptorsWrapper(
        onRequest: (options, handler) {
          print('Fazendo requisição pra: \${options.uri}');
          return handler.next(options);
        },
        onResponse: (response, handler) {
          print('Resposta recebida: \${response.data}');
          return handler.next(response);
        },
        onError: (error, handler) {
          print('Deu ruim: \${error.message}');
          return handler.next(error);
        },
      ),
    );
  }
}
```

### 3. Fazendo uma requisição GET

Agora que o Dio tá na mão, vamos usar ele. Aqui vai um exemplo de como buscar uns posts.

```dart
import 'dart:convert';
import 'package:flutter/material.dart';
import 'dio_client.dart';

class HomePage extends StatefulWidget {
  @override
  _HomePageState createState() => _HomePageState();
}

class _HomePageState extends State<HomePage> {
  final DioClient _dioClient = DioClient();

  List<dynamic> _posts = [];

  Future<void> fetchPosts() async {
    try {
      final response = await _dioClient.dio.get('/posts');
      setState(() {
        _posts = response.data;
      });
    } catch (e) {
      print('Erro ao buscar posts: \$e');
    }
  }

  @override
  void initState() {
    super.initState();
    fetchPosts();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Posts')),
      body: _posts.isEmpty
          ? Center(child: CircularProgressIndicator())
          : ListView.builder(
              itemCount: _posts.length,
              itemBuilder: (context, index) {
                return ListTile(
                  title: Text(_posts[index]['title']),
                  subtitle: Text(_posts[index]['body']),
                );
              },
            ),
    );
  }
}
```

### 4. Testa no emulador ou no dispositivo

Agora é só rodar teu app com `flutter run` e ver a magia acontecer. Certifica que teu dispositivo/emulador tá com internet, ein! 💻📱

## Dica da hora

Sempre trate os erros das requisições pra evitar que o app quebre. E se quiser ir além, dá pra usar o Dio com uns pacotes de gerenciamento de estado tipo Provider ou Riverpod. 

---

E aí, curtiu? Agora é só colocar a mão na massa e dominar as APIs com o Dio. Se der bom (ou ruim), conta pra gente! 🚀

