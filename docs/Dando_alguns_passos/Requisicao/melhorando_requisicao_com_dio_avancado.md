# Dominando o Dio: Exceptions, Interceptors e Encapsulamento ✨

E aí, dev! Bora dar um upgrade no uso do Dio? Nesse artigo, vou te mostrar como tratar exceptions, usar interceptors pra manipular requisições e encapsular o Dio pra deixar teu código mais organizado e profissional. Cola aqui! 😎

---

## Tratando Exceptions

Não adianta fazer requisições se não souber lidar com os erros, né? O Dio já facilita a nossa vida ao lançar exceptions que você pode capturar e tratar com elegância.

Aqui vai um exemplo:

```dart
import 'package:dio/dio.dart';

void fetchData() async {
  final dio = Dio();

  try {
    final response = await dio.get('https://jsonplaceholder.typicode.com/posts/1');
    print('Dados recebidos: \${response.data}');
  } on DioError catch (e) {
    if (e.response != null) {
      print('Erro no servidor: \${e.response?.statusCode} - \${e.response?.data}');
    } else {
      print('Erro na requisição: \${e.message}');
    }
  } catch (e) {
    print('Erro inesperado: \$e');
  }
}
```

### Resumo dos principais tipos de DioError:
- **DioErrorType.connectTimeout**: Timeout de conexão.
- **DioErrorType.sendTimeout**: Timeout ao enviar os dados.
- **DioErrorType.receiveTimeout**: Timeout ao receber os dados.
- **DioErrorType.response**: Erro no lado do servidor.
- **DioErrorType.cancel**: Requisição cancelada.
- **DioErrorType.other**: Qualquer outro erro (exemplo: sem internet).

---

## Usando Interceptors

Interceptors são como "porteiros" das suas requisições. Eles permitem:
- Modificar a requisição antes de ela ser enviada;
- Manipular as respostas antes de entregá-las;
- Tratar erros de forma global.

### Exemplo prático:

```dart
import 'package:dio/dio.dart';

class CustomInterceptors extends InterceptorsWrapper {
  @override
  void onRequest(RequestOptions options, RequestInterceptorHandler handler) {
    print('Interceptando requisição: \${options.uri}');
    options.headers['Authorization'] = 'Bearer MEU_TOKEN';
    super.onRequest(options, handler);
  }

  @override
  void onResponse(Response response, ResponseInterceptorHandler handler) {
    print('Interceptando resposta: \${response.statusCode}');
    super.onResponse(response, handler);
  }

  @override
  void onError(DioError err, ErrorInterceptorHandler handler) {
    print('Interceptando erro: \${err.message}');
    super.onError(err, handler);
  }
}

void main() {
  final dio = Dio();
  dio.interceptors.add(CustomInterceptors());

  dio.get('https://jsonplaceholder.typicode.com/posts/1');
}
```

---

## Encapsulando o Dio

Encapsular o Dio é como colocar uma roupinha bonita nele. Assim, você centraliza a configuração e o uso, deixando o código mais limpo e fácil de manter.

### Criando um cliente encapsulado

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

  DioClient() {
    _dio.interceptors.add(
      InterceptorsWrapper(
        onRequest: (options, handler) {
          print('Requisição para \${options.uri}');
          return handler.next(options);
        },
        onResponse: (response, handler) {
          print('Resposta recebida: \${response.statusCode}');
          return handler.next(response);
        },
        onError: (error, handler) {
          print('Erro capturado: \${error.message}');
          return handler.next(error);
        },
      ),
    );
  }

  Future<Response> get(String endpoint, {Map<String, dynamic>? params}) async {
    try {
      return await _dio.get(endpoint, queryParameters: params);
    } on DioError catch (e) {
      throw Exception('Erro na requisição GET: \${e.message}');
    }
  }

  Future<Response> post(String endpoint, {dynamic data}) async {
    try {
      return await _dio.post(endpoint, data: data);
    } on DioError catch (e) {
      throw Exception('Erro na requisição POST: \${e.message}');
    }
  }
}
```

### Usando o Dio encapsulado

```dart
void main() async {
  final dioClient = DioClient();

  try {
    final response = await dioClient.get('/posts', params: {'userId': 1});
    print('Posts: \${response.data}');
  } catch (e) {
    print('Erro ao buscar posts: \$e');
  }
}
```

---

## Finalizando

Pronto, dev! Agora você tá armado até os dentes pra lidar com requisições HTTP no Flutter usando o Dio. Encapsula tudo, trata os erros e usa interceptors pra mandar aquele toque profissional. Se curtiu ou quer explorar mais alguma coisa, chama aí! 🚀

