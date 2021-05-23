# Colocando Imagens em Seus Projetos

## Primeiro: Imagem como Widget e Imagem como `ImageProvider`

Umas das formas de trabalharmos com imagens dentro do Flutter é considerando ela como um Widget (classe `Image`) ou apenas como uma classe `ImageProvider`. Por enquanto, você apenas precisa saber que isso existe. Primeiro, vamos entender as fontes que podemos pegar nossas imagens!

### `Assets`

Sim, podemos pegar imagens do próprio diretório em nosso computador. É muito comum criarmos uma pasta separada em nosso projeto e chamarmos de `assets` para guadarmos as imagens.

</br>

Porém, para que consigamos colocar essas imagens, precisamos definir em nosso `pubspec.yaml` o caminho que estamos utilizando para guardar nossas imagens. <p>
E é muito simples fazer isso! Veja:

```yaml
flutter:
  assets:
    - assets/images/ #local das nossas imagens
```

### `Network`

Assim como podemos utilizar imagens salvas em nosso computador, também podemos pegar da internet! A vantagem é que não precisamos configurar nada no pubspec. Basta chamarmos a função necessária e passar a url da imagem como argumento.

<br>

Trabalhando com `ImageProvider`:

Dessa classe, duas funções são bem utilizadas: `AssetImage()` e `NetworkImage()`. Ambas recebem String como argumento. Porém, em AssetImage passamos o caminho da imagem, enquanto em NetworkImage passamos a url da imagem.

```dart
Container(
    decoration: BoxDecoration(
        image: DecorationImage(
            image: AssetImage('../../assets/imagem.png'), // com o BoxDecoration, acessamos o atríbuto image, que nos permite utilizar o DecorationImage. A partir disso, podemos utilizar um outro atríbuto image. Este, portanto, recebe um ImageProvider.
        ),
    ),
);
```

```dart
Container(
    decoration: BoxDecoration(
        image: DecorationImage(
            image: NetworkImage('https://urldaimagemdesejada.com/imagem.png'),
        ),
    ),
);
```

```dart
Center(
      child: CircleAvatar(
        radius: 70,
        backgroundImage: NetworkImage('https://d2eip9sf3oo6c2.cloudfront.net/tags/images/000/001/245/thumb/flutterlogo.png'),
      backgroundColor: Colors.purpleAccent[700],
      ),
    );

// O backgroundImage do CircleAvatar também recebe um ImageProvider
```

<br>

Travalhando com a classe `Image`:

Diferente do ImageProvider, a classe Image nos diponibiliza os seguintes métodos semelhantes às funções vistas anteriormente: o `Image.asset()` e o `Image.network()`.

```dart
Container(
    height: 100,
    width: 100,
    child: Image.asset('../../assets/imagem.png',
        fit: BoxFit.fill,
    ),
);
// Sabemos que o child recebe um Widget. E, como podemos ver, estamos passando a classe Image com o método asset para esse atríbuto.
```

```dart
Container(
    height: 100,
    width: 100,
    child: Image.network('https://urldaimagemdesejada.com/imagem.png',
        fit: BoxFit.fill,
    ),
);
```

```dart
Column(
    children: [
        Container(
            height: 100,
            width: 100,
            child: Image.asset('../../assets/imagem.png',
                fit: BoxFit.fill,
            ),
        ),
        Container(
            height: 100,
            width: 100,
            child: Image.asset('../../assets/imagem2.png',
                fit: BoxFit.fill,
            ),
        ),
        Image.asset('../../assets/imagem.png'),
        Image.netowork('https://imagensaletorias.com/img.png'),
        // Perceba que também é possível chamar a classe Image, independente do método utilizado, para uma lista de Widgets, por exemplo.
],
);
```
