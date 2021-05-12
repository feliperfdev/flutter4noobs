# A Importância da Programação Orientada a Objetos no Flutter

## O que é Programação Orientada a Objetos (POO) - Resumo

É um dos que chamamos de `paradigmas da programação`. A Orientação a Objetos é uma forma de representarmos coisas/objetos do mundo real em nossos códigos. Por exemplo:

Quando queremos representar uma pessoa, podemos criar o que chamamos de `classe`. Na línguagem `Dart`, poderiamos escrever da seguinte forma:

```dart
class Pessoa {    // essa é a classe que servirá para representar qualquer pessoa

    String nome;
    int idade;
    double altura;
    // Assim como no mundo real, uma pessoa possui características próprias. Podemos então trazer esse tipo de informação para o código.

    Pessoa({ this.nome, this.idade, this.altura}); // Isso é o que chamamos de construtor da classe.
}

void main() {
    final programador = Pessoa(
        nome: 'Felipe',
        idade: 19,
        altura: 1.82,
    ); // Aqui criamos o que chamamos de Objeto. Esse Objeto é instanciando com a classe que criamos para poder atribuírmos a ele suas características prórpias (atributos de instância).
}
```

## Herança - Resumo

Muito provavelmente quando você estava estudando POO em alguma linguagem de programação, deve ter ouvido falar sobre `herança`.

Em alguns projetos em que trabalhamos com OO, podemos nos deparar com situações em que teremos `classes pai` e as `classes filhas`. Estas, por sua vez, herdam atríbutos - características - da classe pai.

Utilizando o exemplo anterior, vamos criar o que seria um exemplo de classe filha:

```dart
class Cliente extends Pessoa { // o termo 'extends' é utilizado para informar a classe que estamos herdando

int registro;
Cliente({this.registro});

/*
De fato, quando falamos de um cliente podemos estar nos referindo a alguma pessoa, por exemplo. Logo, a classe Cliente vai herdar atríbutos da classe pessoa.
*/

void comprarAlgo() {
    print('Cliente $nome do registro $registro comprou algo');
}

}
```

## A Orientação a Objetos no Flutter

No Flutter trabalhamos com `Widgets` para componentizar nossa aplicação. Costuma-se dizer que <i> tudo </i> no Flutter é Widget.

Mas qual a relação dos Widgets com Orientação a Objetos? A resposta é simples: `Os Widgets são Classes!` Ou melhor: As classes `HERDAM` Widgets, assumindo assim as suas características.
<br/>
<br/>
Então quando queremos representar em nossa aplicação um cartão, por exemplo, contendo informações de alguém ou alguma coisa, costuma-se criar uma classe para representar o 'escopo' do cartão.

Como no Flutter utilizamos a línguagem Dart, seguiremos com a mesma sintaxe do exemplo anterior:

```dart
class Cartao {
    String nome;
    String banco;
    int codigo;
    List<int> digitos;

    Cartao({this.nome, this.banco, this.codigo, this.digitos});
}
```

Nesse caso, criamos apenas uma classe que define os tipos de informações que esse cartão pode conter. Mas e se caso você quisesse exibí-lo na tela de sua aplicação?

Podemos criar um modelo para exibir as informações do cartão. Para isso, trabalharíamos com Widgets. Sim! Os Widgets podem alterar o estado de variáveis e até de Widgets! Por isso eles são utilizados quando queremos criar coisas visuais dentro de nossa aplicação! Coloque isso em mente: Widgets podem ou não possuir um estado e também podem alterar estados! Ou, como chamados em Flutter, esses são os [Stateless e Stateful Widgets](stateless_e_stateful_widgets.md)
