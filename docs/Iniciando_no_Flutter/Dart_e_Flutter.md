# Dart & Flutter

<p align='center'>
<img src='../../assets/dart.png' width=100 title='Dart'>
<img src='../../assets/flutter.png' width=100 title='Flutter'>
</p>

Bom, antes de mais nada, caso não conheça e queira dar uma olhada sobre a línguagem de programação <strong> Dart </strong>, tem o [Dart4Noobs](https://github.com/pksasso/dart4noobs) aqui da He4rt.

Aqui não será explicado sobre a línguagem Dart em si. E sim sobre sua utilização no framework Flutter.

## Por quê Dart?

Dart é uma línguagem de programação que utiliza o paradigma da Programação Orientada a Objetos (POO) e foi desenvolvida pela Google por volta de 2010. É uma línguagem com sintaxe semelhante ao C, C++, C#, Java, Javascript, então se você vem de alguma dessas línguagens não terá tanta dificuldade de aprender.

<b>Mas qual foi o motivo de terem escolhido Dart para ser a línguagem do Flutter?</b>
A resposta é basicamente pelos motivos de:

- 1 Ser uma línguagem de rápido processamento nas multiplas plataformas
- 2 Ser uma línguagem de fácil entendimento em relação à sua sintaxe
- 3 O Flutter também foi desenvolvido pela Google
- 4 Justamente pelo Dart possuir características comuns de diversas outras línguagens nas quais a comunidade de tecnologia tem bastante familiaridade, a produtividade com sua utilização é aumentada.
- 5 Por ser Orientada a Objetos

## Um exemplo da sintaxe do Dart

```dart
class Objeto {
    String nome;
    double tamanho;
    String cor;

    // construtor da classe
    Objeto({this.nome, this.tamanho, this.cor});
}

void main() {
    Objeto caneca = Objeto(
        nome: 'Caneca',
        tamanho: 7,
        cor: 'Verde',
    );
    print(caneca.cor); // -> Verde
}
```

Veja que é bem parecido com algumas outras línguagens.
