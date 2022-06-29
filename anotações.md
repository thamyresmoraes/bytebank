
## Flutter run key commands

`r` --> Hot reload. 🔥🔥🔥

`R` --> Hot restart.

`h` --> Repeat this help message.

`d` --> Detach (terminate "flutter run" but leave application running).

`c` --> Clear the screen

`q` --> Quit (terminate the application on the device).

## Estrutura do projeto

- Apesar do diretório para android e ios, vamos apenas mexer no arquivo ~/lib/main.dart

# Executando o projeto

    run flutter ou através da IDE

## Start

- void main() => print('Bem vindo ao Bytebank');

- Tudo que estiver dentro de runApp() vai ser apresentado no app

- Qualquer componente com representação visual é chamado de widget

## Exemplo de widget que vai apresentar um texto

 ```
  import 'package:flutter/material.dart';

void main() => runApp(Text(
      'Bem vindo ao Bytebank',
      textDirection: TextDirection.ltr, ///Deve sempre colocar a direção do texto
    ));
```

### Widget no flutter
- Widget representa cada elemento visual da tela no flutter;
- Ao construir uma tela podemos usar 1 ou N widgets;
- Ter em mente que estaremos desenvolvendo na estrutura de uma árvore;


### Enriquecendo o projeto visualmente
  - Cupertino (iOS-style widgets), cujo estilo remete aos produtos da Apple, e Material Components, cujos componentes são relacionados ao Material Design da Google.

  Neste projeto vamos usar o Material Components

```
   void main() => runApp(MaterialApp(home: Scaffold()));
 ```

 Criando um appbar :
 ```
 void main() => runApp(
      MaterialApp(
        home: Scaffold(
          appBar: AppBar(),
        ),
      ),
    );
 ```

 Por causa do material Components, não precisamos passar o direcionamento do texto:

 void main() => runApp(
      MaterialApp(
        home: Scaffold(
          appBar: AppBar(title: Text('Transferências')),
        ),
      ),
    );

O que estiver body entra na parte vazia do app


## Estrutura básica das transferências:

```
import 'package:flutter/material.dart';

void main() => runApp(
      MaterialApp(
          home: Scaffold(
        body: Column(
          children: [
            Card(
              child: ListTile(
                leading: Icon(Icons.monetization_on),
                title: Text('200'),
                subtitle: Text('1000'),
              ),
            ),
            Card(
              child: ListTile(
                leading: Icon(Icons.monetization_on),
                title: Text('300'),
                subtitle: Text('7000'),
              ),
            ),
            Card(
              child: ListTile(
                leading: Icon(Icons.monetization_on),
                title: Text('400'),
                subtitle: Text('500'),
              ),
            ),
          ],
        ),
        appBar: AppBar(title: Text('Transferências')),
        floatingActionButton: FloatingActionButton(
          onPressed: () {},
          child: Icon(Icons.add),
        ),
      )),
    );
```

### Técnicas de extração de código

Criando a classe listaTRansferencias

- Diferença entre StetelessWidget e StetefulWidget:
  - Ambas tem o comportamente em encapsular o código;
  - StatefulWidget: Capacidade de modificar o conteúdo de maneira dinâmica;
  - StatelessWidget: Não consegue modificar o conteúdo;

## navegando até uma página com button

  floatingActionButton: FloatingActionButton(
        onPressed: () {
          Navigator.push(context, MaterialPageRoute(builder: (context) {
            return FormularioTransferencia();
          }));
        },