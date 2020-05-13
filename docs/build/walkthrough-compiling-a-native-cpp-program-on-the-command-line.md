---
title: 'Tutorial: Compilar un programa nativo de C++ en la línea de comandos'
description: Utilice el compilador de Microsoft C++ desde un símbolo del sistema.
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335230"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>Tutorial: Compilar un programa nativo de C++ en la línea de comandos

Visual Studio incluye un compilador de línea de comandos C y C++. Puede usarlo para crear todo, desde aplicaciones de consola básicas hasta aplicaciones de la Plataforma universal de Windows, aplicaciones de escritorio, controladores de dispositivos y componentes de .NET.

En este tutorial, creará un programa C++ básico de estilo "Hola, mundo" mediante un editor de texto y, a continuación, compilarlo en la línea de comandos. Si desea probar el IDE de Visual Studio en lugar de usar la línea de comandos, vea [Tutorial: Trabajar con proyectos y soluciones (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) o Usar el IDE de Visual Studio para el desarrollo de [escritorios de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

En este tutorial, puede usar su propio programa C++ en lugar de escribir el que se muestra. O bien, puede usar un ejemplo de código C++ de otro artículo de ayuda.

## <a name="prerequisites"></a>Prerrequisitos

Para completar este tutorial, debe haber instalado Visual Studio y el desarrollo de escritorio opcional con carga de trabajo **de C++** o las herramientas de compilación de línea de comandos para Visual Studio.

Visual Studio es un entorno de *desarrollo integrado* (IDE). Es compatible con un editor completo, administradores de recursos, depuradores y compiladores para muchos lenguajes y plataformas. Las versiones disponibles incluyen la edición gratuita de Visual Studio Community y todas pueden admitir el desarrollo de C y C++. Para obtener información sobre cómo descargar e instalar Visual Studio, vea [Instalar compatibilidad con C++ en Visual Studio](vscpp-step-0-installation.md).

Las herramientas de compilación para Visual Studio instala solo los compiladores de línea de comandos, herramientas y bibliotecas que necesita para compilar programas C y C++. Es perfecto para construir laboratorios o ejercicios en el aula e instala relativamente rápido. Para instalar solo las herramientas de línea de comandos, busque Herramientas de compilación para Visual Studio en la página Descargas de [Visual Studio.](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)

Antes de poder crear un programa C o C++ en la línea de comandos, compruebe que las herramientas están instaladas y puede acceder a ellas desde la línea de comandos. Visual C++ tiene requisitos complejos para que el entorno de línea de comandos encuentre las herramientas, los encabezados y las bibliotecas que utiliza. **No puede usar Visual C++ en una ventana** de símbolo del sistema sin realizar alguna preparación. Afortunadamente, Visual C++ instala accesos directos para iniciar un símbolo del sistema para desarrolladores que tiene el entorno configurado para compilaciones de línea de comandos. Desafortunadamente, los nombres de los accesos directos del símbolo del sistema para desarrolladores y dónde se encuentran son diferentes en casi todas las versiones de Visual C++ y en diferentes versiones de Windows. La primera tarea del tutorial es encontrar la correcta para usar.

> [!NOTE]
> Un acceso directo del símbolo del sistema para desarrolladores establece automáticamente las rutas de acceso correctas para el compilador y las herramientas, así como para los encabezados y bibliotecas necesarios. Debe establecer estos valores de entorno usted mismo si utiliza una ventana **de símbolo del sistema** normal. Para más información, vea [Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](setting-the-path-and-environment-variables-for-command-line-builds.md). Le recomendamos que utilice un acceso directo del símbolo del sistema para desarrolladores en lugar de crear el suyo propio.

### <a name="open-a-developer-command-prompt"></a>Abra un símbolo del sistema para desarrolladores

1. Si ha instalado Visual Studio 2017 o posterior en Windows 10, abra el menú Inicio y elija **Todas las aplicaciones**. Desplácese hacia abajo y abra la carpeta **de Visual Studio** (no la aplicación de Visual Studio). Elija **Developer Command Prompt for VS para** abrir la ventana del símbolo del sistema.

   Si ha instalado Microsoft Visual C++ Build Tools 2015 en Windows 10, abra el menú **Inicio** y elija **Todas las aplicaciones**. Desplácese hacia abajo y abra la carpeta Herramientas de compilación de **Visual C++.** Elija **Visual C++ 2015 x86 Native Tools Símbolo del sistema** para abrir la ventana del símbolo del sistema.

   También puede usar la función de búsqueda de Windows para buscar "símbolo del sistema para desarrolladores" y elegir uno que coincida con la versión instalada de Visual Studio. Utilice el acceso directo para abrir la ventana del símbolo del sistema.

1. A continuación, compruebe que el símbolo del sistema para desarrolladores de Visual C++ está configurado correctamente. En la ventana del `cl` símbolo del sistema, ingrese y verifique que la salida se vea algo como esto:

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   Puede haber diferencias en el directorio actual o los números de versión. Estos valores dependen de la versión de Visual C++ y de las actualizaciones instaladas. Si la salida anterior es similar a la que ve, está listo para compilar programas C o C++ en la línea de comandos.

   > [!NOTE]
   > Si recibe un error como "'cl' no se reconoce como un comando interno o externo, programa operable o archivo por lotes", **`cl`** error C1034 o error LNK1104 al ejecutar el comando, entonces no está utilizando un símbolo del sistema para desarrolladores o algo está mal con la instalación de Visual C++. Debe solucionar este problema antes de poder continuar.

   Si no puede encontrar el acceso directo del símbolo del sistema `cl`para desarrolladores, o si recibe un mensaje de error al escribir , la instalación de Visual C++ puede tener un problema. Intente reinstalar el componente Visual C++ en Visual Studio o vuelva a instalar las herramientas de compilación de Microsoft Visual C++. No vaya a la siguiente sección **`cl`** hasta que el comando funcione. Para obtener más información acerca de la instalación y solución de problemas de Visual C++, vea [Instalar Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > Según la versión de Windows en el equipo y la configuración de seguridad del sistema, es posible que tenga que hacer clic con el botón derecho para abrir el menú contextual del acceso directo del símbolo del sistema para desarrolladores y, a continuación, elija **Ejecutar como administrador** para compilar y ejecutar correctamente el programa que cree siguiendo este tutorial.

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Cree un archivo de origen de Visual C++ y compílelo en la línea de comandos

1. En la ventana del `md c:\hello` símbolo del sistema para `cd c:\hello` desarrolladores, escriba para crear un directorio y, a continuación, escriba para cambiar a ese directorio. Este directorio es donde se crean el archivo de origen y el programa compilado.

1. Escriba `notepad hello.cpp` en la ventana del símbolo del sistema.

   Elija **Sí** cuando el Bloc de notas le pida que cree un archivo. Este paso abre una ventana del Bloc de notas en blanco, lista para que escriba el código en un archivo denominado hello.cpp.

1. En el Bloc de notas, introduzca las siguientes líneas de código:

   ```cpp
   #include <iostream>
   using namespace std;
   int main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   Este código es un programa simple que escribirá una línea de texto en la pantalla y luego saldrá. Para minimizar los errores, copie este código y péguelo en el Bloc de notas.

1. No olvide guardar su trabajo. En el Bloc de notas, en el menú **Archivo** , elija **Guardar**.

   Enhorabuena, ha creado un archivo de código fuente de C++, hello.cpp, que está listo para compilar.

1. Vuelva a la ventana del símbolo del sistema para desarrolladores. Ingrese `dir` en el símbolo del sistema para enumerar el contenido del directorio c:-hello. Debería ver el archivo de origen hello.cpp en la lista de directorios, que tiene un aspecto similar a:

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

   Las fechas y otros detalles diferirán en su computadora. Si no ve el archivo de código fuente, *hello.cpp*, asegúrese de que ha cambiado al directorio *\\c: hello* que ha creado. En el Bloc de notas, asegúrese de que ha guardado el archivo de origen en este directorio. Asegúrese también de que ha *`.cpp`* guardado el código *`.txt`* fuente con una extensión de nombre de archivo, no con una extensión.

1. En el símbolo del `cl /EHsc hello.cpp` sistema para desarrolladores, escriba para compilar el programa.

   El compilador cl.exe genera un archivo .obj que contiene el código compilado y, luego, ejecuta el enlazador para crear un programa ejecutable llamado hello.exe. Este nombre aparece en las líneas de información de salida que muestra el compilador. La salida del compilador debe tener un aspecto similar a:

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
   > Si recibe un error como "'cl' no se reconoce como un comando interno o externo, programa operable o archivo por lotes", error C1034 o error LNK1104, el símbolo del sistema para desarrolladores no está configurado correctamente. Para obtener información sobre cómo solucionar este problema, vuelva a la sección **Abrir un símbolo del sistema** para desarrolladores.

   > [!NOTE]
   > Si obtiene un error o advertencia de compilador o vinculador diferente, revise el código fuente para corregir los errores y, a continuación, guárdelo y vuelva a ejecutar el compilador. Para obtener información acerca de errores específicos, utilice el cuadro de búsqueda de esta página MSDN para buscar el número de error.

1. Para ejecutar el programa hello.exe, en el símbolo del sistema, escriba `hello`.

   El programa mostrará este texto y se cerrará:

   ```Output
   Hello, world, from Visual C++!
   ```

   Enhorabuena, ha compilado y ejecutado un programa C++ mediante las herramientas de línea de comandos.

## <a name="next-steps"></a>Pasos siguientes

Este ejemplo de "Hola, Mundo" es tan simple como un programa C++ puede obtener. Los programas del mundo real suelen tener archivos de encabezado, más archivos de origen y enlaces a bibliotecas.

Puede usar los pasos de este tutorial para crear su propio código C++ en lugar de escribir el código de ejemplo que se muestra. Estos pasos también le permiten crear muchos programas de ejemplo de código C++ que encontrará en otro lugar. Puede colocar el código fuente y compilar las aplicaciones en cualquier directorio grabable. De forma predeterminada, el IDE de Visual Studio crea proyectos en la carpeta de usuario, en una subcarpeta *de repositorios\\* de origen. Las versiones anteriores pueden colocar proyectos en una versión de *Documents\\Visual Studio \<>\\ *carpeta Projects*.

Para compilar un programa que tenga archivos de código fuente adicionales, introdúzcalos todos en la línea de comandos, como:

`cl /EHsc file1.cpp file2.cpp file3.cpp`

La `/EHsc` opción de línea de comandos indica al compilador que habilite el comportamiento estándar de control de excepciones C++. Sin él, las excepciones producidas pueden dar lugar a objetos no destruidos y fugas de recursos. Para obtener más información, consulte [/EH (Modelo de control de excepciones)](reference/eh-exception-handling-model.md).

Al proporcionar archivos de origen adicionales, el compilador utiliza el primer archivo de entrada para crear el nombre del programa. En este caso, se genera un programa llamado file1.exe. Para cambiar el nombre a program1.exe, agregue una opción de vinculador [/out:](reference/out-output-file-name.md)

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Y para detectar más errores de programación automáticamente, le recomendamos compilar mediante la opción de nivel de advertencia [/W3](reference/compiler-option-warning-level.md) o [/W4:](reference/compiler-option-warning-level.md)

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

El compilador, cl.exe, tiene muchas más opciones. Puede aplicarlos para compilar, optimizar, depurar y analizar el código. Para obtener una `cl /?` lista rápida, escriba en el símbolo del sistema para desarrolladores. También puede compilar y vincular por separado y aplicar opciones de vinculador en escenarios de compilación más complejos. Para obtener más información sobre las opciones y el uso del compilador y del vinculador, consulte Referencia de creación de [C/C++.](reference/c-cpp-building-reference.md)

Puede usar NMAKE y makefiles, MSBuild y archivos de proyecto, o CMake, para configurar y compilar proyectos más complejos en la línea de comandos. Para obtener más información sobre el uso de estas herramientas, vea [NMAKE Reference](reference/nmake-reference.md), [MSBuild](msbuild-visual-cpp.md)y [CMake proyectos en Visual Studio](cmake-projects-in-visual-studio.md).

Los idiomas C y C+ son similares, pero no los mismos. El compilador MSVC usa una regla simple para determinar qué lenguaje usar cuando compila el código. De forma predeterminada, el compilador MSVC *`.c`* trata los archivos que terminan *`.cpp`* como código fuente de C y los archivos que terminan como código fuente de C++. Para forzar al compilador a tratar todos los archivos como C++ independientemente de la extensión de nombre de archivo, utilice la opción del compilador [/TP.](reference/tc-tp-tc-tp-specify-source-file-type.md)

El compilador MSVC incluye una biblioteca en tiempo de ejecución de C (CRT) que se ajusta al estándar ISO C99, con excepciones menores. El código portátil generalmente se compila y se ejecuta según lo esperado. Ciertas funciones de biblioteca obsoletas y varios nombres de función POSIX están en desuso por el compilador MSVC. Se admiten las funciones, pero los nombres preferidos han cambiado. Para obtener más información, consulte Características de [seguridad en CRT](../c-runtime-library/security-features-in-the-crt.md) y Advertencia del compilador [(nivel 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Consulte también

[Referencia del idioma C++](../cpp/cpp-language-reference.md)<br/>
[Proyectos y sistemas de compilación](projects-and-build-systems-cpp.md)<br/>
[Opciones del compilador de MSVC](reference/compiler-options.md)
