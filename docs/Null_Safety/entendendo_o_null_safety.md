# Entendendo o Null Safety

<p align='center'>
<img src='../../assets/nullsafety.png' height=280>
<p/>



## Dart 2.12

A versão 2.12 do Dart trouxe uma novidade incrível para a línguagem: o `Null Safety`. Uma feature que veio para fortalecer o sistema de tipagens do Dart e facilitar a captura de erros por valores nulos, que é um dos principais motivos de *crashes* causados em aplicativos durante o desenvolvimento.

## Valores Nullable e Non-Nullable

Com o Null Safety, o Dart ganhou dois novos operadores: o `?` e o `!`. Mais para frente veremos a diferença entre o `?` e o `??`.
A questão é: para que servem e como devem ser utilizados?

Primeiramente vamos precisar entender o que acontece quando migramos finalmente para o Null Safety. A partir de agora, **o sistema de declaração de variáveis muda e o padrão dos tipos é `Non-Nullable` (não nulos)**.  Ou seja, por padrão, não poderemos mais ter variáveis nulas, pelo menos não da forma como conheciamos.

## Permitindo que uma variável seja nula - Operador **`?`**

Bom, agora que temos por padrão no Dart as variáveis `Non-Nullable`, foi definido um operador para permitirmos que, pelo menos por algum momento, as variáveis possam ter um valor nulo. Esse operador é o `?`. Utilizamos ele dessa forma:

```dart
String? nome;
```

Dessa forma estamos permitindo que a variável `nome` possa ser, durante um determinado momento, nula. Ou melhor dizendo, **estamos permitindo que ela seja nula até que seja instanciada / receba algum valor não nulo**.

```dart
String? nome;

void setUserSettings(Settings settings) {
    nome = "Nome da Pessoa"; // Variável recebeu valor não nulo.
    
    settings.updateName(nome);
}

```

## Utilizando o **`required`**

Na criação de classes no Dart devemos também pensar um pouco além em algumas situações. Por exemplo: "O que pode ser nulo?", "O que não pode ser nulo?", "O que é obrigatório que todo objeto dessa classe tenha?". Esses são pensamentos que provavelmente sempre tivemos, mas agora temos formas melhores de trabalharmos com eles.

Como sou muito fã de Pokémon, irei utilizar a classe `Pokemon` como exemplo.

Um pokémon possui um número/id da pokédex (`dexNum`), um nome (`name`) e **pode ou não** ter uma evolução (`evolution`). Ou seja, `dexNum` e `name` serão necessariamente atributos OBRIGATÓRIOS para essa classe, enquanto `evolution` poderá ser **Nullable** já que podem existir Pokémon sem alguma evolução. Logo, para algum Pokémon, esse atributo só deixará de ser nulo se o mesmo possuir evolução.

Como sabemos que `dexNum` e `name` são atributos obrigatórios, utilizamos no construtor da nossa classe a palavra reservada **`required`** para definirmos que estes são obrigatórios na criação de um objeto da classe `Pokemon`.

```dart
class Pokemon {
    final int dexNum;
    final String name;
    final String? evolution;

    const Pokemon({
        required this.dexNum,
        required this.name,
        this.evolution,
    });
}
```

```dart
final pikachu = Pokemon(
    dexNum: 25,
    name: "Pikachu",
    evolution: "Raichu",
);

final greninja = Pokemon(
    dexNum: 658,
    name: "Greninja",
);
```

No exemplo acima, o Pokémon **Pikachu** possui evolução, por isso o atributo `evolution` é preenchido com o nome de sua evolução.

Situação diferente para o Pokémon **Greninja**, que não possui evolução. Logo, o atributo de `evolution` para ele permanece nulo.

## Trabalhando com o operador **`!`**

Utilizamos esse operador quando temos a certeza de que alguma variável ou atributo de classe que PODE ser nulo(a) possui um valor não nulo.

Vamos utilizar um pokémon dos exemplos acima:

```dart
final pikachu = Pokemon(
    dexNum: 25,
    name: "Pikachu",
    evolution: "Raichu",
);
```

Sabemos que `evolution` é um atributo **Nullable**, ou seja, pode ser nulo.

```dart
String printPikachuInfo() {
    String info = "${pikachu.name} --> ${pikachu.evolution!}";
    return info;
}
```

Perceba o operador `!` em **`pikachu.evolution!`**. Isso devido ao fato de sabermos que o atributo `evolution` da variável `pikachu`, que é um atributo que pode ser nulo, possui um valor não nulo.

## Utilizando o operador **`??`**

A explicação para esse operador é mais simples. Utilizamos ele como uma forma de executarmos algo quando algum valor for nulo.

```dart
final controller = PokemonController();

Image pokemonSprite = controller.getSprite();

.
.
.

Container(
    decoration: BoxDecoration(
        image: DecorationImage(
            image: pokemonSprite.image ?? Image.asset('customSprite.png').image,
        ),
    ),
),
```

No exemplo acima, estamos informando que caso o getter `image` da variável `pokemonSprite` seja nulo, será utilizado um `Image.asset().image` no lugar.

## Inicialização tardia: **late**

O `late` é um modificador que permite que o valor de uma variável, inicialmente, seja NULO (`Nullable`).

```dart
late TaskController controller;
/// A variável `controller` da classe [TaskController] está sendo considerada, inicialmente, nula.
///
```

O `late` é uma forma de permitir que a variável seja inicializada / instanciada tardiamente.

Vamos para um exemplo demonstrando a inicialização tardia:

```dart
late TaskRepository repository;

Future<List<Task>> getAllTasks() async {
    repository = TaskRepository(); // Variável foi inicializada aqui

    final taskList = await repository.getTasks();
    return taskList;
}
```

---
