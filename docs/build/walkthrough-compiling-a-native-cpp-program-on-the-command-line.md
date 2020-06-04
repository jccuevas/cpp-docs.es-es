---
title: 'Tutorial: Compilación de un programa nativo de C++ en la línea de comandos'
description: Use el compilador de Microsoft C++ desde un símbolo del sistema.
ms.custom: conceptual
ms.date: 04/02/2020
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
ms.openlocfilehash: c24fdfdaef612059d5c2fbaaa58f10d83f5fe3a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335230"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>Tutorial: Compilación de un programa nativo de C++ en la línea de comandos

Visual Studio incluye una línea de comandos de C y un compilador de C++. Puede usarlo para crear desde aplicaciones de consola básicas hasta aplicaciones de la Plataforma universal de Windows, de escritorio, controladores de dispositivos y componentes de .NET.

En este tutorial, creará un programa de consola de C++ básico de estilo "Hola mundo" con un editor de texto y, luego, lo compilará en la línea de comandos. Si quiere probar el IDE de Visual Studio en lugar de usar la línea de comandos, vea [Tutorial: Trabajar con proyectos y soluciones (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) o [Uso del IDE de Visual Studio para desarrollo de escritorio con C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

En este tutorial, puede usar programas de C++ propios en lugar de escribir el que se muestra. O bien, puede usar un ejemplo de código de C++ de otro artículo de ayuda.

## <a name="prerequisites"></a>Requisitos previos

Para completar este tutorial, debe haber instalado Visual Studio y la carga de trabajo opcional **Desarrollo de escritorio con C++** , o bien las herramientas de compilación de línea de comandos para Visual Studio.

Visual Studio es un *entorno de desarrollo integrado* (IDE). Admite un editor completo, administradores de recursos, depuradores y compiladores para varios lenguajes y plataformas. Las versiones disponibles incluyen la edición gratuita de Visual Studio Community y todas pueden admitir el desarrollo para C y C++. Para obtener información sobre cómo descargar e instalar Visual Studio, vea [Instalación de compatibilidad con C++ en Visual Studio](vscpp-step-0-installation.md).

Las herramientas de compilación para Visual Studio solo instalan los compiladores de línea de comandos, las herramientas y las bibliotecas que necesita para compilar programas de C y C++. Resultan perfectas para laboratorios de compilación o ejercicios en aulas, y se instalan con relativa rapidez. Para instalar solo las herramientas de línea de comandos, busque Herramientas de compilación para Visual Studio en la página [Descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019).

Antes de poder compilar un programa de C o C++ en la línea de comandos, compruebe que las herramientas están instaladas y que puede acceder a ellas desde la línea de comandos. Visual C++ tiene requisitos complejos para que el entorno de línea de comandos busque las herramientas, los encabezados y las bibliotecas que usa. **No se puede usar Visual C++ en una ventana del símbolo del sistema sin formato** sin cierta preparación. Afortunadamente, Visual C++ instala accesos directos para que pueda iniciar un símbolo del sistema para desarrolladores con el entorno configurado para compilaciones de línea de comandos. Desafortunadamente, los nombres de los accesos directos del símbolo del sistema para desarrolladores y dónde se encuentran son diferentes en casi todas las versiones de Visual C++ y en versiones diferentes de Windows. La primera tarea del tutorial es encontrar el correcto.

> [!NOTE]
> Un acceso directo del símbolo del sistema para desarrolladores establece automáticamente las rutas de acceso correctas para el compilador y las herramientas, y para los encabezados y las bibliotecas necesarios. Debe establecer estos valores de entorno manualmente si usa una ventana de **símbolo del sistema** normal. Para más información, vea [Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](setting-the-path-and-environment-variables-for-command-line-builds.md). Se recomienda usar un acceso directo del símbolo del sistema para desarrolladores en lugar de crear uno propio.

### <a name="open-a-developer-command-prompt"></a>Apertura de un símbolo del sistema para desarrolladores

1. Si ha instalado Visual Studio 2017 o una versión posterior en Windows 10, abra el menú Inicio y elija **Todas las aplicaciones**. Desplácese hacia abajo y abra la carpeta **Visual Studio** (no la aplicación Visual Studio). Elija **Símbolo del sistema para desarrolladores de VS** para abrir la ventana del símbolo del sistema.

   Si ha instalado Microsoft Visual C++ Build Tools 2015 o una versión posterior en Windows 10, abra el menú **Inicio** y elija **Todas las aplicaciones**. Desplácese hacia abajo y abra la carpeta **Visual C++ Build Tools**. Elija **Símbolo del sistema de las herramientas nativas x86 de Visual C++ 2015** para abrir la ventana del símbolo del sistema.

   También puede usar la función de búsqueda de Windows para buscar "símbolo del sistema para desarrolladores" y elegir uno que coincida con la versión instalada de Visual Studio. Use el acceso directo para abrir la ventana del símbolo del sistema.

1. Después, compruebe que el símbolo del sistema para desarrolladores de Visual C++ está configurado correctamente. En la ventana del símbolo del sistema, escriba `cl` y compruebe que la salida es similar a la siguiente:

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   Es posible que haya diferencias en el directorio actual o en los números de versión. Estos valores dependen de la versión de Visual C++ y de las actualizaciones instaladas. Si la salida anterior es similar a lo que ve, está listo para compilar programas de C o C++ en la línea de comandos.

   > [!NOTE]
   > Si recibe un error como ""cl" no se reconoce como un comando interno o externo, programa o archivo por lotes ejecutable", C1034 o LNK1104 al ejecutar el comando **`cl`** , significa que no usa un símbolo del sistema para desarrolladores o que hay algún problema con la instalación de Visual C++. Debe corregir este error para poder continuar.

   Si no encuentra el acceso directo del símbolo del sistema para desarrolladores, o si recibe un mensaje de error al escribir `cl`, es posible que la instalación de Visual C++ tenga un problema. Intente volver a instalar el componente Visual C++ en Visual Studio, o bien vuelva a instalar Microsoft Visual C++ Build Tools. No pase a la sección siguiente hasta que el comando **`cl`** funcione. Para obtener más información sobre cómo instalar y solucionar problemas de Visual C++, vea [Instalación de Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > En función de la versión de Windows del equipo y de la configuración de seguridad del sistema, es posible que deba abrir el menú contextual del símbolo del sistema para desarrolladores y, después, elegir **Ejecutar como administrador** para compilar y ejecutar correctamente el programa que se crea siguiendo este tutorial.

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Creación de un archivo de código fuente de Visual C++ y compilarlo en la línea de comandos

1. En la ventana del símbolo del sistema para desarrolladores, escriba `md c:\hello` para crear un directorio y, después, escriba `cd c:\hello` para cambiar a ese directorio. En este directorio se crean el archivo de código fuente y el programa compilado.

1. Escriba `notepad hello.cpp` en la ventana del símbolo del sistema.

   Elija **Sí** cuando el Bloc de notas le pida que cree un archivo. En este paso se abre una ventana del Bloc de notas en blanco, lista para que escriba el código en un archivo denominado hello.cpp.

1. En el Bloc de notas, escriba las líneas de código siguientes:

   ```cpp
   #include <iostream>
   using namespace std;
   int main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   Este código es un programa sencillo que escribirá una línea de texto en la pantalla y, después, saldrá. Para minimizar los errores, copie este código y péguelo en el Bloc de notas.

1. No olvide guardar su trabajo. En el Bloc de notas, en el menú **Archivo** , elija **Guardar**.

   Enhorabuena, ha creado un archivo de código fuente de C++, hello.cpp, que está listo para compilarse.

1. Cambie a la ventana del símbolo del sistema para desarrolladores. Escriba `dir` en el símbolo del sistema para mostrar el contenido del directorio c:\hello. Debería ver el archivo de código fuente hello.cpp en la lista de directorios, con un aspecto similar al siguiente:

   ```Output
   c:\hello>dir
    Volume in drive C has no label.
    Volume Serial Number is CC62-6545

    Directory of c:\hello

   05/24/2016  05:36 PM    <DIR>          .
   05/24/2016  05:36 PM    <DIR>          ..
   05/24/2016  05:37 PM               115 hello.cpp
                  1 File(s)            115 bytes
                  2 Dir(s)  571,343,446,016 bytes free

   ```

   Las fechas y otros detalles serán distintos en su equipo. Si no ve el archivo de código fuente, *hello.cpp*, asegúrese de que ha cambiado al directorio *c:\\hello* que ha creado. En el Bloc de notas, asegúrese de que ha guardado el archivo de código fuente en este directorio. Asegúrese también de que ha guardado el código fuente con una extensión de nombre de archivo *`.cpp`* , no una extensión *`.txt`* .

1. En el símbolo del sistema para desarrolladores, escriba `cl /EHsc hello.cpp` para compilar el programa.

   El compilador cl.exe genera un archivo .obj que contiene el código compilado y, luego, ejecuta el enlazador para crear un programa ejecutable llamado hello.exe. Este nombre aparece en las líneas de información de salida que muestra el compilador. La salida del compilador debe ser similar a la siguiente:

   ```Output
   c:\hello>cl /EHsc hello.cpp
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   hello.cpp
   Microsoft (R) Incremental Linker Version 14.10.25017.0
   Copyright (C) Microsoft Corporation.  All rights reserved.

   /out:hello.exe
   hello.obj
   ```

   > [!NOTE]
   > Si obtiene un error, como ""cl" no se reconoce como un comando interno o externo, programa o archivo por lotes ejecutable", C1034 o LNK1104, el símbolo del sistema para desarrolladores no está correctamente configurado. Para obtener información sobre cómo corregir este problema, vuelva a la sección **Apertura de un símbolo del sistema para desarrolladores**.

   > [!NOTE]
   > Si recibe otra advertencia o error del compilador o del enlazador, revise el código fuente para corregir los errores, guárdelo y vuelva a ejecutar el compilador. Para obtener información sobre los errores específicos, use el cuadro de búsqueda de esta página de MSDN para buscar el número de error.

1. Para ejecutar el programa hello.exe, en el símbolo del sistema, escriba `hello`.

   El programa mostrará este texto y se cerrará:

   ```Output
   Hello, world, from Visual C++!
   ```

   Enhorabuena, ha compilado y ejecutado un programa de C++ con las herramientas de línea de comandos.

## <a name="next-steps"></a>Pasos siguientes

Este ejemplo "Hola mundo" es el programa de C++ más sencillo que se puede crear. Los programas del mundo real suelen tener archivos de encabezado, más archivos de código fuente y vínculos a bibliotecas.

Puede usar los pasos de este tutorial para crear código de C++ propio en lugar de escribir el del ejemplo que se muestra. Estos pasos también permiten crear muchos programas de ejemplo de código de C++ que encontrará en otras partes. Puede colocar el código fuente y compilar las aplicaciones en cualquier directorio en el que se pueda escribir. De forma predeterminada, el IDE de Visual Studio crea los proyectos en la carpeta de usuario, en una subcarpeta *source\\repos*. En versiones anteriores, es posible que los proyectos se guarden en una carpeta *Documents\\Visual Studio \<versión>\\* Projects*.

Para compilar un programa que tiene archivos de código fuente adicionales, escríbalos todos en la línea de comandos, de esta forma:

`cl /EHsc file1.cpp file2.cpp file3.cpp`

La opción de línea de comandos `/EHsc` indica al compilador que habilite el comportamiento estándar de control de excepciones de C++. Sin él, las excepciones iniciadas pueden producir pérdidas de recursos y objetos sin destruir. Para obtener más información, consulte [/EH (Modelo de control de excepciones)](reference/eh-exception-handling-model.md).

Cuando se suministran archivos de código fuente adicionales, el compilador usa el primer archivo de entrada para crear el nombre del programa. En este caso, genera un programa llamado file1.exe. Para cambiar el nombre a program1.exe, agregue una opción del enlazador [/out](reference/out-output-file-name.md):

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Y para detectar más errores de programación de forma automática, se recomienda compilar mediante la opción de nivel de advertencia [/W3](reference/compiler-option-warning-level.md) o [/W4](reference/compiler-option-warning-level.md):

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

El compilador, cl.exe, tiene muchas más opciones. Puede aplicarlas para compilar, optimizar, depurar y analizar el código. Para obtener una lista rápida, escriba `cl /?` en el símbolo del sistema para desarrolladores. También puede compilar y vincular por separado, y aplicar las opciones del enlazador en escenarios de compilación más complejos. Para obtener más información sobre el uso y las opciones del compilador y del enlazador, vea [Referencia de compilación de C/C++](reference/c-cpp-building-reference.md).

Puede usar NMAKE y archivos Make, MSBuild y archivos del proyecto, o CMake, para configurar y compilar proyectos más complejos en la línea de comandos. Para obtener más información sobre el uso de estas herramientas, vea [Referencia de NMAKE](reference/nmake-reference.md), [MSBuild](msbuild-visual-cpp.md) y [Proyectos de CMake en Visual Studio](cmake-projects-in-visual-studio.md).

Los lenguajes C++ C y son similares, pero no idénticos. El compilador de MSVC utiliza una regla simple para determinar qué lenguaje se usa al compilar el código. De forma predeterminada, el compilador de MSVC trata todos los archivos que finalizan en *`.c`* como código fuente de C y los que finalizan en *`.cpp`* como código fuente de C++. Para hacer que el compilador trate todos los archivos como de C++ con independencia de la extensión del nombre de archivo, use la opción [/TP](reference/tc-tp-tc-tp-specify-source-file-type.md) del compilador.

El compilador de MSVC incluye una Biblioteca en tiempo de ejecución de C (CRT) que se ajusta al estándar ISO C99, con excepciones menores. Normalmente, el código portable se compila y se ejecuta según lo previsto. Algunas funciones de biblioteca obsoletas y varios nombres de funciones POSIX están en desuso en el compilador de MSVC. Las funciones se admiten, pero los nombres preferidos han cambiado. Para obtener más información, vea [Características de seguridad de CRT](../c-runtime-library/security-features-in-the-crt.md) y [Advertencia del compilador (nivel 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Proyectos y sistemas de compilación](projects-and-build-systems-cpp.md)<br/>
[Opciones del compilador de MSVC](reference/compiler-options.md)
