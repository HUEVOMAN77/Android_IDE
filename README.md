# NovaIDE

**Desarrollá aplicaciones Android desde tu teléfono.** NovaIDE es un fork comunitario de [CodeOnTheGo](https://github.com/appdevforall/CodeOnTheGo), el sucesor de AndroidIDE, mantenido en este repositorio por **HUEVOMAN77**.

Este es el repositorio de **NovaIDE**. Es un proyecto independiente: no es la distribución oficial de CodeOnTheGo ni de AndroidIDE. Conservamos el reconocimiento y las licencias del trabajo original.

## Descargar NovaIDE

**Versión recomendada: [v0.1.1](https://github.com/HUEVOMAN77/Android_IDE/releases/tag/v0.1.1).** Los dos archivos están publicados en las Releases de **este fork**; los enlaces siguientes descargan directamente desde este repositorio, no desde el sitio del proyecto original.

| Archivo | Descarga directa | Tamaño aproximado |
| --- | --- | --- |
| App para Android de 64 bits | **[Descargar NovaIDE-arm64-debug.apk](https://github.com/HUEVOMAN77/Android_IDE/releases/download/v0.1.1/NovaIDE-arm64-debug.apk)** | 75 MB |
| Herramientas y entorno de ejecución | **[Descargar assets-arm64-v8a.zip](https://github.com/HUEVOMAN77/Android_IDE/releases/download/v0.1.1/assets-arm64-v8a.zip)** | **1.1 GB** |

**Necesitás ambos archivos para completar la instalación.** La APK de esta versión es una compilación de prueba firmada (`debug`) y no incluye el entorno de ejecución dentro del instalador.

> Usá **v0.1.1**, no la APK de prueba de v0.1.0: esa primera publicación usó una firma diferente. La versión recomendada conserva la firma de la primera APK de NovaIDE que se entregó desde este fork.

## Requisitos

- Teléfono o tablet con **Android 9 o superior** y procesador **arm64-v8a**.
- Espacio libre para el zip de 1.1 GB, los archivos que se extraen y las dependencias de tus proyectos.
- Conexión a internet para la descarga inicial; se recomienda Wi-Fi por el tamaño del entorno.
- Permisos solicitados por la app, como acceso a archivos e instalación de las APK que compiles.

Esta entrega no es para Windows ni para dispositivos x86 o de 32 bits. Podés descargar los archivos en una computadora y transferirlos, pero **la app se instala y se usa en el teléfono**.

## Instalación en el teléfono

1. Descargá **`assets-arm64-v8a.zip`** desde el enlace de arriba.
2. Dejalo **sin descomprimir** en esta ubicación del almacenamiento interno:

   ```text
   /storage/emulated/0/Download/assets-arm64-v8a.zip
   ```

   Es la misma ruta que `/sdcard/Download/assets-arm64-v8a.zip`. El administrador de archivos puede mostrar la carpeta como **Download** o **Descargas**. No lo pongás en una subcarpeta ni cambies el nombre; evitá sufijos como `(1)`.

3. Descargá e instalá **`NovaIDE-arm64-debug.apk`**. Si Android lo solicita, permití instalar desde la app con la que abriste el archivo.
4. Abrí **NovaIDE**, otorgá los permisos necesarios y completá la instalación. La app busca el zip en esa ruta e importa el entorno de ejecución; la extracción puede tardar varios minutos.
5. Cuando termine, ya podés continuar con la configuración y tus proyectos.

Si ya tenés la primera APK de **este fork**, instalá v0.1.1 encima de ella: **no hace falta desinstalar**. Se conservaron el paquete y la firma para permitir la actualización. Una instalación de AndroidIDE o CodeOnTheGo firmada por otra distribución no necesariamente admite esa actualización.

## ¿Para qué sirve el zip de 1.1 GB?

No es otro instalador ni un proyecto de ejemplo. Es el paquete de recursos que necesita la APK `debug` para preparar el IDE dentro del teléfono.

Incluye estos componentes:

- SDK de Android.
- Distribución de Gradle y su API.
- Repositorio Maven local con dependencias.
- Bootstrap de Termux y componentes del entorno integrado.
- Base de documentación para consulta sin conexión.
- Paquetes de plugins y la colección de plantillas `core.cgt`.

La separación evita meter todo ese contenido dentro de una APK enorme. **No lo extraigás manualmente:** NovaIDE se encarga de importarlo durante la instalación inicial.

Una vez preparado el entorno, algunas tareas pueden hacerse sin conexión. Descargar nuevas dependencias, usar servicios de IA externos o acceder a repositorios remotos sigue requiriendo internet.

## Si aparece «No se encontró el archivo de assets»

El mensaje indica que la app no encuentra el zip donde lo espera. No significa por sí solo que el IDE esté dañado.

Verificá lo siguiente:

- La descarga terminó: el archivo completo pesa aproximadamente **1.1 GB**.
- El nombre es exactamente **`assets-arm64-v8a.zip`**.
- Está en **Download del almacenamiento interno del teléfono**, no solamente en las Descargas de la computadora, en una tarjeta SD o dentro de otra carpeta.
- No lo descomprimiste ni quedó con un nombre como `assets-arm64-v8a (1).zip`.
- Otorgaste el acceso a archivos que solicita NovaIDE.

Después de colocarlo correctamente, cerrá y volvé a abrir NovaIDE, y completá la instalación. Si el error continúa, conservá una captura del mensaje y los datos de tu dispositivo para revisar el caso.

## Mejoras implementadas en este fork

| Cambio | Qué aporta |
| --- | --- |
| **Marca NovaIDE** | Nombre visible de la app, textos del producto, información de versión y saludo del entorno con la identidad del fork. |
| **Español latino** | Se completaron y revisaron **1.736 recursos de texto**, incluidos permisos, errores, editor, herramientas de depuración, Termux, ajustes de IA y plugins. También se tradujeron plurales y listas de instrucciones. |
| **Idioma sin limitarlo a España** | Los recursos usan español genérico (`values-es`) en lugar de depender de `values-es-rES`, para que puedan aplicarse en configuraciones latinoamericanas. |
| **Botones y pantallas sin textos fijos en inglés** | Se pasaron a recursos traducibles controles de selección de contexto, archivos, modelos locales y vista previa de Markdown, incluidos varios mensajes de ese plugin. |
| **Compilación propia en GitHub Actions** | Se preparó un workflow para generar la APK arm64 y el zip, con SDK/NDK, dependencias, cachés y memoria ajustada al runner. |
| **Firma original estable** | La clave se conserva como secreto cifrado de Actions, no depende de una caché de una rama y su certificado se verifica antes de compilar. Así las builds de ramas y tags usan la misma identidad. |
| **Entrega completa en Releases** | La APK y el zip de **1.1 GB** se publican juntos desde el runner de GitHub, con instrucciones de instalación y enlaces de descarga en este README. |

Se mantiene **`com.itsaky.androidide`** como identificador del paquete. No se renombraron las rutas de proyectos ni los archivos de configuración heredados para evitar romper datos existentes.

El **`targetSdk` permanece en 28 de forma deliberada**. Con un objetivo 29 o superior, Android 10 y versiones posteriores restringen la ejecución de binarios escritos por la app, lo que afecta al JDK, Gradle y la terminal integrados. Esto es distinto del SDK usado para compilar el IDE, que está en **36**.

### Funciones heredadas del proyecto original

La base CodeOnTheGo ya incluye edición de proyectos Android, terminal integrada con Termux, soporte para Java y Kotlin, integración con Git, plugins, vistas previas y herramientas de depuración. El servidor de lenguaje Kotlin también viene del proyecto original: **no se presenta como una función creada por este fork**.

## Estado de la versión

- **CI de v0.1.1 completado correctamente:** [ver la compilación](https://github.com/HUEVOMAN77/Android_IDE/actions/runs/43768953852).
- Recursos de español, formatos de texto y XML comprobados; los recursos modificados se compilaron con AAPT2.
- APK arm64 firmada y certificado original verificado.
- APK y entorno publicados en las Releases de este repositorio.
- **La prueba completa en el teléfono sigue pendiente.** Estos controles no garantizan que todas las funciones heredadas, la compilación de cada proyecto o las herramientas de depuración funcionen en todos los dispositivos.

La documentación incorporada, los mensajes que generan herramientas externas y el contenido de tus proyectos pueden conservar su idioma original; no forman parte de la traducción de la interfaz.

## Código y compilación

El código con los cambios de NovaIDE está en la rama **[novaide/inicio](https://github.com/HUEVOMAN77/Android_IDE/tree/novaide/inicio)**. No necesitás clonar ni compilar el repositorio para instalar los archivos de la release.

```bash
git clone --branch novaide/inicio https://github.com/HUEVOMAN77/Android_IDE.git
```

El [workflow de NovaIDE](https://github.com/HUEVOMAN77/Android_IDE/blob/novaide/inicio/.github/workflows/novaide-build.yml) prepara el entorno y ejecuta las tareas de la variante arm64:

```bash
./gradlew :app:assetsDownloadDebug --no-daemon --max-workers=4
./gradlew :app:assembleV8Debug :app:assembleV8Assets --no-daemon --max-workers=4
```

El CI usa JDK 17, SDK de compilación 36 y la configuración de NDK del proyecto. La publicación de actualizaciones de este fork requiere el secreto de firma configurado por quien mantiene el repositorio; **la clave privada no está en el código fuente ni en las Releases**.

Para colaborar, revisá la [guía de contribuciones heredada](./CONTRIBUTING.md) y la [arquitectura del proyecto](./ARCHITECTURE.md). Esos documentos conservan el contenido del proyecto original y no necesariamente están traducidos.

## Reconocimientos

Este fork se apoya en el trabajo de **App Dev for All / CodeOnTheGo** y de la comunidad de [AndroidIDE](https://github.com/AndroidIDEOfficial/AndroidIDE). Se conservan las licencias y los reconocimientos de los componentes originales.

Agradecimientos a:

- Akash Yadav, por [AndroidIDE](https://github.com/AndroidIDEOfficial/AndroidIDE).
- Rosemoe, por [CodeEditor](https://github.com/Rosemoe/sora-editor).
- La comunidad de [Termux](https://github.com/termux), por su [emulador de terminal](https://github.com/termux/termux-app).
- Bogdan Melnychuk, por [AndroidTreeView](https://github.com/bmelnychuk/AndroidTreeView).
- George Fraser, por [Java Language Server](https://github.com/georgewfraser/java-language-server).
- Vivek, por [LayoutEditor](https://github.com/itsvks19/LayoutEditor).
- [Apache Software Foundation](https://www.apache.org) y todas las personas que contribuyeron al proyecto y sus dependencias.

## Documentación de terceros y sus licencias

Se mantienen los reconocimientos de los materiales incluidos por el proyecto original:

- **Java, Java, Java: Object-Oriented Problem Solving, Third Edition**, de R. Morelli y R. Walde, anteriormente publicado por Pearson Education. Distribuido bajo **CC BY 4.0**. [Fuente](https://open.umn.edu/opentextbooks/textbooks/java-java-java-object-oriented-problem-solving).
- **Android Notes for Professionals**: [Goalkicker](https://goalkicker.com/AndroidBook/).
- **Java Notes for Professionals**: [Goalkicker](https://goalkicker.com/JavaBook/).
- **Kotlin Notes for Professionals**: [Goalkicker](https://goalkicker.com/KotlinBook/).
- Documentación de herramientas de desarrollo Android: [fuente](https://developer.android.com), licencia [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
- Documentación de Kotlin: [fuente](https://kotlinlang.org/), licencia [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
- Documentación de OpenJDK: [fuente](https://packages.debian.org/unstable/openjdk-17-doc), licencia [Debian Open Publications](https://www.debian.org/opl).

Los títulos y nombres propios se conservan para identificar correctamente sus fuentes. La documentación de terceros se mantiene sin modificar.

## Licencia

NovaIDE es software libre bajo **GNU GPL versión 3 o posterior**. Podés redistribuirlo y modificarlo según sus condiciones.

Se distribuye con la intención de que sea útil, pero **sin garantía**, incluida cualquier garantía implícita de comerciabilidad o adecuación para un propósito particular. Consultá el texto completo en [LICENSE](./LICENSE) y las condiciones de cada dependencia.
