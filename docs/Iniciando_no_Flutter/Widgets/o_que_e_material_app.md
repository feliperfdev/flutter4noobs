# O que é o Material App

Como foi dito, o Flutter é um framework voltado para o desenvolvimento cross-platform. Suas aplicações utilizam o MaterialApp ou o [CuppertinoApp](o_que_e_cupertino_app.md) para a construção de um 'WidgetApp', adicionando funcionalidades específicas dessas classes aos apps.
Essas duas classes são as responsáveis por inicializarem nossos apps, por isso são associadas à função runApp dentro do escopo da main( ).

```dart

void main() => runApp(ExampleApp());

class ExampleApp extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
        return MaterialApp(
            debugShowCheckedModeBanner: false,
            title: 'Example App',
            home: HomePage(),
            routes: {},
        );
    }
}
```

### Alguns Widgets específicos do MaterialApp

- Scaffold
- MaterialPageRoute
- AnimatedTheme
- GridPaper
