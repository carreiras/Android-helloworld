# Projeto 1: Helloworld

A seguir, mostraremos como evoluir o exemplo de Hello World para incluir uma caixa de texto (EditText). Quando o usuário digitar o nome e pressionar Enter, atualizaremos a mensagem exibida na tela.

## Estrutura do projeto

```
MeuProjetoHelloWorld
├─ app
│  ├─ src
│  │  ├─ main
│  │  │  ├─ java
│  │  │  │  └─ com.example.helloworld
│  │  │  │     └─ MainActivity.kt
│  │  │  └─ res
│  │  │     └─ layout
│  │  │        └─ activity_main.xml
│  │  └─ AndroidManifest.xml
└─ build.gradle
```

## Layout: activity_main.xml
Modifique o layout para incluir um EditText onde o usuário digita o nome e um TextView que exibirá a mensagem.

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <!-- Campo de texto para o usuário digitar o nome -->
    <EditText
        android:id="@+id/etName"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Digite seu nome"
        android:imeOptions="actionDone"
        android:inputType="textPersonName"
        android:gravity="center"
        android:layout_margin="16dp" />

    <!-- Texto que exibirá o Hello World, incrementado com o nome -->
    <TextView
        android:id="@+id/tvHelloMessage"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        android:textSize="24sp"
        android:layout_marginTop="16dp" />
</LinearLayout>
```

- LinearLayout: Um contêiner linear para agrupar elementos.
- EditText (@+id/etName): onde o usuário digita o nome.
- TextView (@+id/tvHelloMessage): exibe a mensagem que inclui o nome digitado.

## Classe MainActivity.kt
No onCreate, recuperamos as referências dos componentes e configuramos o listener para detectar quando o usuário pressiona Enter (a ação EditorInfo.IME_ACTION_DONE).

```
package com.example.helloworld

import android.os.Bundle
import android.view.inputmethod.EditorInfo
import androidx.appcompat.app.AppCompatActivity
import android.widget.EditText
import android.widget.TextView

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Referências para os componentes do layout
        val etName = findViewById<EditText>(R.id.etName)
        val tvHelloMessage = findViewById<TextView>(R.id.tvHelloMessage)

        // Listener para quando o usuário pressiona Enter (actionDone)
        etName.setOnEditorActionListener { textView, actionId, _ ->
            if (actionId == EditorInfo.IME_ACTION_DONE) {
                val name = textView.text.toString().trim()
                // Verifica se o nome foi digitado
                if (name.isNotEmpty()) {
                    tvHelloMessage.text = "Hello World, $name!"
                } else {
                    tvHelloMessage.text = "Hello World!"
                }
                true // Indica que consumimos o evento
            } else {
                false
            }
        }
    }
}
```
## Principais pontos:

- val etName = findViewById<EditText>(R.id.etName): Obtemos a referência do EditText.
- setOnEditorActionListener { ... }: Captura quando o usuário pressiona Enter no teclado.
- EditorInfo.IME_ACTION_DONE: Significa que o botão de ação do teclado foi configurado para "Concluir" (Done).
- Atualizamos o TextView com "Hello World, $nome!" se o usuário digitou algo. Se o EditText estiver vazio, mantemos "Hello World!".

## Resultado
- Ao rodar o aplicativo, será exibido um campo para digitar o nome e, abaixo, a mensagem Hello World! inicial.
- Quando o usuário digitar o nome e pressionar Enter, a mensagem mudará para “Hello World, [NomeDoUsuário]!”.