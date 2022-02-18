# Aplicando Null Safety no Flutter

## Migration

---
## Situação problema

Vamos supor que você ou a empresa na qual você trabalha está desenvolvendo uma aplicação com um backend. Independente do tamanho desse backend, nossa aplicação pode sim acabar recebendo um valor nulo vindo dele.

Imagine: um usuário do aplicativo não colocou uma foto de perfil, portanto, esse campo ficou setado como `null`.

Podemos imaginar que essa situação nos traria o seguinte exemplo de código para a imagem de perfil do usuário:

```dart

print(user.profile.image) // -> null

Container(
    decoration: BoxDecoration(
        image: DecorationImage(
            image: Image.network(user.profile.image).image, // null
        ),
    ),
),

```

Xiiii!! Que perigo! Imagine só o `Image.network()` recebendo um valor nulo? Exatamente: isso não faz sentido ou, melhor, não é o ideal, pelo menos.