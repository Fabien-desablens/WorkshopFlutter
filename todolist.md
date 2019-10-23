Pour commencer on va importer le package material, qui va nous permettre d'utiliser un paquet de widgets déjà construits.

```dart
import 'package:flutter/material.dart';
``` 

Le code exécuté en Dart commence toujours par la fonction main(), nous allons donc la créer et éxecuter le component qui contient notre application.
En Flutter tous les components sont appelés "Widgets".

```dart
void main() => runApp(new MyApp());
``` 

Nous allons créer un Widget stateless qui sera le container de notre app.

```dart
class MyApp extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
        return Container();
    }
}
``` 
Et dedans nous allons utiliser le Widget material "MaterialApp()".
On va pouvoir y mettre le titre de notre app et créer une structure basique avec un titre et un widget qui sera le corps de notre app.

```dart
class MyApp extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
        return new MaterialApp(
          title: 'Todo List',
          home: TodoListScreen(),
        );
    }
}
``` 

On va donc créer ce widget stateful qui servira à render la todo list

```dart
class TodoListScreen extends StatefulWidget {
  @override
  _TodoListState createState() => _TodoListState();
}

class _TodoListStateScreenState extends State<TodoListScreen> {
  @override
  Widget build(BuildContext context) {
    return Container();
  }
}
``` 

Qui va retourner un widget Scaffold, ce widget sert à créer une structure simple.

On va y intégrer: 
* une appbar
* un body
* unbouton flottant

```dart
class _TodoListStateScreenState extends State<TodoListScreen> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Todo List')),
      body: TodoList(
        todos: todos,
        onTodoToggle: _toggleTodo,
      ),
      floatingActionButton: FloatingActionButton(
        child: Icon(Icons.add),
        onPressed: _addTodo,
      ),
    );
  }
}
```

Et créer les fonctions qui serviront dans le Widget.

* 

```dart
class _TodoListStateScreenState extends State<TodoListScreen> {

  _addTodo() async {
    final todo = await showDialog<Todo>(
      context: context,
      builder: (BuildContext context) {
        return NewTodoDialog();
      },
    );
  }


  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Todo List')),
      body: TodoList(
        todos: todos,
        onTodoToggle: _toggleTodo,
      ),
      floatingActionButton: FloatingActionButton(
        child: Icon(Icons.add),
        onPressed: _addTodo,
      ),
    );
  }
}
```