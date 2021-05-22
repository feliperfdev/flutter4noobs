# Criando uma AppBar do Zero

<b>Aviso: Essa AppBar foi retirada de um código já pronto que fiz na NLW #5 - Mas o que importa mesmo está apenas nas 4 primeiras linhas :)</b>

Primeiramente, se você for no atríbuto `appBar` do Scafold em seu projeto, verá que ele recebe um `PreferredSizeWidget`. </br>
Então, para criarmos um Widget desse tipo, criamos uma classe e colocamos ela para herdar um `PreferredSize`.

<br>

A partir disso, chamamos a própria classe utilizando o construtor da <b>classe herdada</b> através de um `super()`. Esse super trará todos os atríbutos contidos na classe `PreferredSize` para utilizarmos e criarmos nossa AppBar da forma que quisermos!

```dart
class CustomAppBar extends PreferredSize {
  CustomAppBar()
      : super(
          preferredSize: Size.fromHeight(250),
          child: Container(
            height: 250,
            child: Stack(
              children: [
                Container(
                  padding: EdgeInsets.symmetric(horizontal: 20),
                  decoration: BoxDecoration(gradient: AppGradients.linear),
                  height: 161,
                  width: double.maxFinite,
                  child: Row(
                    mainAxisAlignment: MainAxisAlignment.spaceBetween,
                    children: [
                      RichText(
                          text: TextSpan(
                        text: 'Olá, ',
                        style: AppTextStyles.title,
                        children: [
                          TextSpan(
                              text: 'Felipe Ribeiro!',
                              style: AppTextStyles.titleBold)
                        ],
                      )),
                      Container(
                        height: 58,
                        width: 58,
                        decoration: BoxDecoration(
                          borderRadius: BorderRadius.circular(10),
                          border:
                              Border.all(color: Color(0xFF7149CD), width: 2),
                          image: DecorationImage(
                              image: NetworkImage(AppImages.profilePic)),
                        ),
                      ),
                    ],
                  ),
                ),
                Align(
                  alignment: Alignment.bottomCenter,
                  child: ScoreCard(),
                ),
              ],
            ),
          ),
        );
}
```

Por fim, com esse código, teremos um resultado semelhante a esse. Mas, lembre-se, você pode personalizar sua AppBar da forma que desejar, deixando-a do tamanho, formato, comportamento que quiser!

<div align='center'>
    <img src='../../../assets/appbar_devquiz_felipe.jpg' width=350>
</div>
