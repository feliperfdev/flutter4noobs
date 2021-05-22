# Icon

Basicamente, como o nome já diz, é um Widget que trabalha com `ícones`! Para ser mais exato, duas classes serão importantes aqui: a `Icon` e a `Icons`.

Basicamente, para chamarmos um ícone em nossa tela, precisamos do Widget `Icon`, que recebe a classe `Icons` e também permite mudarmos cor, tamanho e outras características dos ícones.

```dart
body: Center(
        child: Row(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Icon(Icons.arrow_back_ios, color: Colors.purple, size: 30),
            Icon(Icons.mobile_off, color: Colors.purple, size: 30),
            Icon(Icons.favorite, color: Colors.purple, size: 30),
          ],
        ),
      ),
```

<div align='center'>
    <img src='../../../assets/icons.jpg' height=400>
</div>

<br>

# IconButton
