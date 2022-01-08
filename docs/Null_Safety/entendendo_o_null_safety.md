# Entendendo o Null Safety

<p align='center'>
<img src='../../assets/nullsafety.png' height=280>
<p/>



## Dart 2.12

A versão 2.12 do Dart trouxe uma novidade incrível para a línguagem: o `Null Safety`. Uma feature que veio para fortalecer o sistema de tipagens do Dart e facilitar a captura de erros por valores nulos, que é um dos principais motivos de *crashes* causados em aplicativos durante o desenvolvimento.

## Valores Nullable e Non Nullable

Com o Null Safety, o Dart ganhou dois novos operadores: o `?` e o `!`. Mais para frente veremos a diferença entre o `?` e o `??`.
A questão é: para que servem e como devem ser utilizados?

Primeiramente vamos precisar entender o que acontece quando migramos finalmente para o Null Safety. A partir de agora, **o sistema de declaração de variáveis muda e o padrão dos tipos é `Non-Nullable` (não nulos)**. 

## Permitindo que um valor seja nulo - Operador '?'


```dart
class Game {
    final String? id;
    final String? name;
    final double? price;

    const Game({
        this.id,
        this.name,
        this.price,
    });
}
```

## Inicialização tardia: **late**

O `late` é um modificador que permite que o valor de uma variável, inicialmente, seja NULO (`Nullable`).

```dart
late TaskController controller;
/// A variável `controller` da classe [TaskController] está sendo considerada, inicialmente, nula.
///
/// O `late` é uma forma de permitir que a variável seja inicializada / instanciada tardiamente.
```

Vamos para um exemplo demonstrando a inicialização tardia:

```dart
late TaskController controller;

Future<List<Task>> getAllTasks() async {
    controller = TaskController(); // Variável foi inicializada aqui

    final taskList = await controller.getTasks();
    return taskList;
}
```

---
