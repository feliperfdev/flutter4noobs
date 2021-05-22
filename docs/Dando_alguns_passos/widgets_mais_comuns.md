# Widgets Mais Comuns

<div align='center'>
    <i>
        <b>
            Neste tópico, iremos tratar de alguns Widgets que comumente são utilizados nos apps desenvolvidos com Flutter!
        </b>
    </i>
</div>

</br>
</br>
<b>Não esqueça de ler os comentários dos código ^-^</b>
</br>
</br>

---

## Container

O container é um dos Widgets mais utilizados nas aplicações. É ele que na maioria das vezes utilizamos para criar cards, formatos, botões personalizados, dimensionamentos, posicionamentos, artes dentre várias outras possibilidades que temos.
Nele podemos determinar uma altura, uma largura, cor, bordas (tamanho da borda, cor, arredondamento da borda...), gradiente, espaçamento para dentro (padding) ou para fora (margin), sombreamento... São várias possibilidades!

Exemplo de um Container:

```dart
// OBS: Lembre-se que ao passar o mouse por cima dos atríbutos ou das classes/Widgets, você pode ver os parâmetro que recebe e o tipo de retorno

final estiloTexto = TextStyle(
    color: Colors.white,
    fontSize: 20,
  );

Container(
    height: 200,
    width: 200,
    alignment: Aligment.center, // aqui estamos definindo a centralização dos elementos filhos do container
    child Text('Flutter4Noobs', style: estiloTexto), // o conteúdo (elementos filhos) do Container é apenas um texto escrito 'Flutter4Noobs'
    decoration: BoxDecoration(
        shape: BoxShape.circle, // formato do container
        gradient: LinearGradient(
            begin: Alignment.topRight,
            end: Alignment.bottomLeft
            colors: <Color>[
                Color(0xffee0000),
                Color(0xffeeee00)
              ],
        ),
    ),
    /*
    OBS: Ao colocarmos o mouse por cima da classe Colors quando estamos utilizando alguma cor, podemos ver uma paleta de cores contendo a intensidade de cada uma.

    Exemplo:
    Colors.purple[300] => estamos pegando a cor roxa na intensidade 300.
    */
),
```

<b>Resultado:</b> </br>
<img src='../../assets/container1.jpg'/>

---

## Column & Row (Coluna e Linha)

Uma coisa muito comum nos apps são linhas e colunas.

Por exemplo: Ícones alinhados (como os ícones de reações nas redes sociais).
<br/><img src='../../assets/row-twitter.jpg' title='Ícones do twitter'> <br/>
Neste caso, provavelmente poderia ter sido feito com uma Row (`linha`), ou com algum componente que permite alinhar os ícones dessa forma.

Mas agora vamos para o código. O que será mostrado são apenas exemplos, nada muito complexo, apenas para o entendimento de como funciona as Columns e as Rows.

MAS, antes, precisamos entender três coisas desses Widgets:

- MainAxisAlignment
- CrossAxisAlignment
- children

<b>MainAxisAlignment</b>

<div align='center'>

</div>

<b>CrossAxisAlignment</b>

<div align='center'>

</div>

<b>children</b>

<div align='center'>

</div>

`Coluna (Column)`

```dart
  final cont = Container(
    height: 50,
    width: 50,
    color: Colors.purpleAccent,
  );

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.spaceEvenly,
          children: [
            cont,
            cont,
            cont,
          ],
        ),
      ),
    );
  }
```

<br/>
<img src='../../assets/column.jpg' height=360>
<br/><br/>

`Linha (Row)`

```dart
  final cont = Container(
    height: 50,
    width: 50,
    color: Colors.purpleAccent,
  );

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Row(
          mainAxisAlignment: MainAxisAlignment.spaceEvenly,
          children: [
            cont,
            cont,
            cont,
          ],
        ),
      ),
    );
  }
```

<br/>
<img src='../../assets/row.jpg' height=360>
<br/><br/>

---

## AvatarCircle

---

## Icon
