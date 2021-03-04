# O que é o Cupertino App

Assim como o [MaterialApp](o_que_e_material_app.md), o CupertinoApp também é utilizado para a construção de um 'WidgetApp', adicionando funcionalidades específicas do Cupertino aos apps.

```dart

void main() => runApp(ExampleApp());

class ExampleApp extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
        return CupertinoApp(
  routes: <String, WidgetBuilder>{
    '/': (BuildContext context) {
      return CupertinoPageScaffold(
        navigationBar: CupertinoNavigationBar(
          middle: const Text('Home Route'),
        ),
        child: Center(child: Icon(CupertinoIcons.share)),
      );
    },
    '/about': (BuildContext context) {
      return CupertinoPageScaffold(
        navigationBar: CupertinoNavigationBar(
          middle: const Text('About Route'),
        ),
        child: Center(child: Icon(CupertinoIcons.share)),
      );
    }
  },
);
    }
}
```

### Alguns Widgets específicos do CupertinoApp

- CupertinoPageScaffold
- CupertinoNavigationBar
- CupertinoIcons
- CupertinoColors
- CupertinoThemeData
- CupertinoPageRoute
