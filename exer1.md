import 'package:flutter/material.dart';

// Ponto de entrada da aplicação Flutter.
void main() {
  // A função runApp infla o widget principal e o anexa à tela.
  runApp(const MeuApp());
}

// O widget principal da aplicação.
// StatelessWidget é um widget que não requer estado mutável.
class MeuApp extends StatelessWidget {
  const MeuApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      // Título da aplicação, visível na aba do navegador.
      title: 'Meu App Dart',
      // Desativa o banner de "Debug" no canto superior direito.
      debugShowCheckedModeBanner: false,
      // Define o tema global da aplicação.
      theme: ThemeData(
        primarySwatch: Colors.green, // Alteração da cor primária
        visualDensity: VisualDensity.adaptivePlatformDensity,
      ),
      // O widget da tela inicial da aplicação.
      home: const TelaPrincipal(),
    );
  }
}

// Widget que representa a tela principal.
class TelaPrincipal extends StatelessWidget {
  const TelaPrincipal({super.key});

  @override
  Widget build(BuildContext context) {
    // Scaffold é um widget que implementa a estrutura visual básica do Material Design.
    return Scaffold(
      // Define a cor de fundo da tela.
      backgroundColor: Colors.grey[100],
      // A barra no topo da aplicação.
      appBar: AppBar(
        title: const Text('Meu App Dart'),
        backgroundColor: Colors.green[700], // Alteração da cor da barra
      ),
      // O corpo principal da tela.
      body: Center(
        // Center é um widget que centraliza seu filho.
        // Column organiza seus filhos em uma coluna vertical.
        child: Column(
          // Alinha os filhos no centro do eixo principal (vertical).
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            // Widget de texto para exibir o nome.
            const Text(
              'Seu Nome Aqui', // Alteração do nome
              style: TextStyle(
                fontSize: 32, // Aumento do tamanho da fonte
                fontWeight: FontWeight.bold,
                color: Colors.green, // Alteração da cor do texto
              ),
            ),
            // Um espaçamento vertical entre os widgets.
            const SizedBox(height: 40),
            // Botão com elevação.
            ElevatedButton(
              // A função a ser executada quando o botão é pressionado.
              onPressed: () {
                // Exibe um diálogo de alerta.
                showDialog(
                  context: context,
                  builder: (BuildContext context) {
                    return AlertDialog(
                      title: const Text('Saudação'),
                      content: const Text('Olá, Programador!'), // Alteração do texto
                      actions: <Widget>[
                        TextButton(
                          child: const Text('Fechar'),
                          onPressed: () {
                            // Fecha o diálogo.
                            Navigator.of(context).pop();
                          },
                        ),
                      ],
                    );
                  },
                );
              },
              style: ElevatedButton.styleFrom(
                backgroundColor: Colors.green, // Cor de fundo do botão
                padding: const EdgeInsets.symmetric(horizontal: 40, vertical: 20),
              ),
              child: const Text(
                'Saudar', // Alteração do texto do botão
                style: TextStyle(fontSize: 20, color: Colors.white),
              ),
            ),
          ],
        ),
      ),
    );
  }
}
