# TextField

Sabe quando vemos em aplicativos alguns campos de texto em que podemos colocar nomes, e-mails, senhas e demais informações? Até mesmo quando queremos escrever algo que tenha uma quantidade maior de linhas?
Pois bem, esses são os famosos `inputs` (digamos que esse seria um nome "global"). No Flutter, chamamos esses inputs de `TextField`!

Nele podemos definir diversos valores como valor/texto inicial, labels, hints, número de linhas, número de caracteres e também podemos decorá-lo com a classe `InputDecoration` para deixar a cara do seu app. Além de podermos associá-lo a um controller (`TextEditingController`) que nos permite manipular o texto inserido no TextField.

<br/>
<div align='center'>
    <i>
        <b>
            Lembre-se de prestar atenção nos comentários dos códigos ^-^
        </b>
    </i>
</div>

<br/>
<br/>

Demonstração da implementação do TextField

```dart
TextField(
  decoration: InputDecoration(
    border: OutlineInputBorder(),
    labelText: 'E-mail',
  ),
)
```

```dart
final _controller = TextEditingController(); // O TextEditingController é um controller utilizado para manipular o texto do TextField
```

```dart
Center(
    child: Container(
        padding: EdgeInsets.all(10),
        /*
        Aqui nós estamos chamando o Widget TextField
        */
        child: TextField(
            obscureText: true, // a propriedade obscureText serve para mascarar o texto, deixando-o com cara de input de senha quando digita
            controller: _controller,
            decoration: InputDecoration(
            border: OutlineInputBorder(),
            labelText: 'Senha',
            ),
            onChanged: (texto) {
                /*
                A propriedade onChanged recebe uma String (texto), e essa String é sempre atualizada quando há alguma alteração no TextField

                Aqui estamos dizendo que o conteúdo do TextFiel (_controller.text) será atualizado com o texto que está sendo digitado.
                */
            setState(() {
                _controller.text = texto;
            });
            }),
    ),
    ),
```

Percebeu como é fácil atualizar o conteúdo de um TextField. O controller serve justamente para auxiliar na manipulação dessa alteração!

O TextEditingController possui um `.text` e `.value` que podemos utilizar para determinados casos em que estamos atualizando o conteúdo do TexField.
Para isso, podemos utilizar o atríbuto onChanged, que recebe uma String que está sendo atualizada constantemente à medida em que digitamos algo. Tendo isso, passamos essa String para o `controller.text` para podermos utilizarmos o texto digitado em algum outro lugar do nosso app.

<img src='../../../assets/password.jpg' height=320>
<img src='../../../assets/password2.jpg' height=320>

<br/>
<br/>

`DICA!! :)` <br/>
Às vezes quando queremos colocar um valor inicial nos inputs (geralmente quando buscamos dados de alguma API ou então quando já vem por padrão do app), é uma ótima ideia usarmos um atributo do TextField chamado de `initialValue` para isso!

Pense bem: Tendo um valor pré-definido e depois associá-lo ao onChanged irá facilitar a manipulação do conteúdo do TextField. Afinal, quando estivermos modificando-o, o initialValue já vai ser atualizado com o novo conteúdo que é passado pela String do onChaned.
