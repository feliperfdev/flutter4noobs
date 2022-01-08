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

## Permitindo que uma variável seja nula - Operador '?'

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

## Utilizando o `required`

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

## Trabalhando com o operador '!'

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
