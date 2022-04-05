# Colocando Imagens em Seus Projetos

É muito comum vermos em diversos aplicativos imagens sendo utilizadas de diversas formas, seja apenas para ilutrar ou pra interação com alguma funcionalidade do aplicativo.
<p>Pois bem!
<p>
Neste tópico do Flutter4Noobs, iremos aprender a como colocar imagens em seu aplicativo! Sejam elas vindas do seu ambiente local ou até mesmo da internet.

---

## Entendendo o `Image`

Primeiro, vamos entender as fontes que podemos pegar nossas imagens!

### `Assets`

Sim, podemos pegar imagens do próprio diretório em nosso computador. É muito comum criarmos uma pasta separada em nosso projeto e chamarmos de `assets` para guadarmos as imagens. Para colocarmos uma imagem dos nossos assets no projeto, basta chamarmos o método `Image.assets()`.

</br>

Porém, para que consigamos colocar essas imagens, precisamos definir em nosso `pubspec.yaml` o caminho que estamos utilizando para guardar nossas imagens. <p>
E é muito simples fazer isso! Veja:

```yaml
flutter:
  assets:
    - assets/images/ #local das nossas imagens
```

### `Network`

Assim como podemos utilizar imagens salvas em nosso computador, também podemos pegar da internet! A vantagem é que não precisamos configurar nada no pubspec. Basta chamarmos a função necessária e passar a url da imagem como argumento. A função, no caso, é a própria `Image.network()`.

<br>

A classe Image nos diponibiliza os seguintes métodos: o `Image.asset()` e o `Image.network()`.

```dart
Container(
    height: 100,
    width: 100,
    child: Image.asset('../../assets/imagem.png',
        fit: BoxFit.fill,
    ),
);
```

No exemplo acima, sabemos que o child recebe um Widget. E, como podemos ver, estamos passando a classe Image com o método asset para esse atríbuto.

```dart
Container(
    height: 100,
    width: 100,
    child: Image.network('https://urldaimagemdesejada.com/imagem.png',
        fit: BoxFit.fill,
    ),
);
```

## Exemplo ilustrativo do uso do Image.network( ):

```dart
class Home extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      appBar: AppBar(),
      body: Center(
        child: Image.network("https://yt3.ggpht.com/ytc/AKedOLRt1d4p7bPylasq_66BIC8-k3hkyVjJ2JICQITK=s900-c-k-c0x00ffffff-no-rj"),
      ),
    );
  }
}
```

<img src='../../assets/screenshots/image_network.png' height=300 width=200>
<p>

Perceba que também é possível chamar a classe Image, independente do método utilizado, para uma lista de Widgets, por exemplo:

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
],
);
```
