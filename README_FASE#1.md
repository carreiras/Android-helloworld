# Projeto 1: Helloworld

A seguir está um exemplo bem simples de um projeto HelloWorld em Android (utilizando Kotlin). Ele consiste em:

- Um layout com um TextView que exibe a mensagem "Hello World".
- Uma Activity principal que carrega esse layout no método onCreate.

## Estrutura básica do projeto

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
No diretório res/layout, crie o arquivo activity_main.xml.

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

    <TextView
        android:id="@+id/textViewHello"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        android:textSize="24sp" />
</LinearLayout>
```

- LinearLayout: Um contêiner linear para agrupar elementos.
- TextView: Exibe o texto "Hello World!".

## Activity Principal: MainActivity.kt
No diretório java/com/example/helloworld/, crie a classe MainActivity.kt.

```
package com.example.helloworld

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle

class MainActivity : AppCompatActivity() {
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        
        // Associa a Activity ao layout definido em activity_main.xml
        setContentView(R.layout.activity_main)
    }
}
```

- onCreate: É o método chamado quando a Activity é criada pela primeira vez.
- setContentView: Carrega o layout que criamos (activity_main.xml).

## Arquivo de Manifesto: AndroidManifest.xml
Certifique-se de que seu AndroidManifest.xml contenha o seguinte (o Android Studio geralmente gera isto automaticamente ao criar o projeto):

```
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.helloworld">

    <application
        android:allowBackup="true"
        android:label="HelloWorld"
        android:supportsRtl="true"
        android:theme="@style/Theme.AppCompat.Light.NoActionBar">

        <!-- Declarando a Activity principal -->
        <activity android:name=".MainActivity">
            <intent-filter>
                <!-- Indica que esta Activity é a tela de entrada (launcher) -->
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>
</manifest>
```

## Executando
No Android Studio, selecione Run (ou o ícone “▶”) para rodar o app no emulador ou dispositivo físico.
Quando o app iniciar, você verá o texto "Hello World!" centralizado na tela.