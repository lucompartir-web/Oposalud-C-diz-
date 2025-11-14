# OpoSalud Cádiz

Aplicación móvil para oposiciones sanitarias en Andalucía.  
Construida con **Google Sheets + Glide** y empaquetada en APK con **Android Studio**.

---

## 📑 Contenido

- Preguntas tipo test (`data/preguntas.csv`)
- Fichas de estudio (`data/fichas.csv`)
- Simulacros de 30 minutos (`data/simulacros.csv`)
- Glosario (`data/glosario.csv`)
- Constitución Española (`data/constitucion.csv`)
- Estatuto de Autonomía de Andalucía (`data/estatuto.csv`)
- Biobancos (`data/biobancos.csv`)

---

## 🚀 Cómo usar

### 1. Preparar datos
- Copia los archivos `.csv` de la carpeta `data/` en tu Google Sheets.
- Cada archivo corresponde a una pestaña distinta.
- Ajusta los simulacros para que `TiempoTotal = 30`.

### 2. Crear la app en Glide
- Entra en [Glide](https://www.glideapps.com).
- Crea una nueva app y conecta tu Google Sheets.
- Configura las pantallas:
  - **Inicio** → accesos rápidos y foco diario.
  - **Estudio** → fichas visuales.
  - **Test** → preguntas filtradas por tema.
  - **Simulacros** → exámenes de 30 minutos.
  - **Glosario** → buscador de términos.
  - **Constitución** → artículos CE.
  - **Estatuto** → artículos del Estatuto.
  - **Biobancos** → preguntas específicas.

### 3. Publicar la app
- Pulsa en **Publish** dentro de Glide.
- Obtén la URL pública (ejemplo: `https://tuapp.glide.page`).
- Instálala en tu móvil como acceso directo (PWA).

### 4. Convertir en APK
- Abre la carpeta `android/` en Android Studio.
- Sustituye la URL en `MainActivity.kt` por la de tu Glide app.
- Compila el proyecto y genera tu APK firmada.
- Instala la APK en tu móvil Android.

---

## 📂 Estructura del repositorio
android/
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/tuusuario/tcaesas/
│   │   │   │   └── MainActivity.kt
│   │   │   ├── res/
│   │   │   │   └── layout/activity_main.xml
│   │   │   └── AndroidManifest.xml
├── build.gradle
└── settings.gradle
package com.tuusuario.tcaesas

import android.os.Bundle
import android.webkit.WebView
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        val webView = WebView(this)
        webView.settings.javaScriptEnabled = true
        webView.loadUrl("https://tcae.glide.page") // ← Aquí pones tu URL de Glide
        setContentView(webView)
    }
}
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.tuusuario.tcaesas">

    <application
        android:label="TCAE SAS App"
        android:theme="@style/Theme.AppCompat.Light.NoActionBar">
        <activity android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
