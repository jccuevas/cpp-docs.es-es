---
title: 'Tutorial: Compilar un programa de C++ nativo en la línea de comandos | Microsoft Docs'
ms.custom: conceptual
ms.date: 09/24/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7f8fad0c4676e8dfedcf8e80332c0a239f230cb
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821197"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>Tutorial: Compilar un programa nativo de C++ en la línea de comandos

Visual C++ incluye un compilador de C++ de línea de comandos que puede usar para crear cualquier cosa desde las aplicaciones de consola básica para aplicaciones de la plataforma Universal de Windows, aplicaciones de escritorio, controladores de dispositivos y componentes. NET.

En este tutorial, creará básico, "Hello, World": programa de C++ de estilo mediante el uso de un texto editor y, a continuación, compilarlo en la línea de comandos. Si desea probar el IDE de Visual Studio en lugar de usar la línea de comandos, consulte [Tutorial: trabajar con proyectos y soluciones (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) o [mediante el IDE de Visual Studio para el desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

En este tutorial, puede usar su propio programa de Visual C++ en lugar de escribir el que se muestra o usar un código de ejemplo de Visual C++ de otro artículo de ayuda.

## <a name="prerequisites"></a>Requisitos previos

Para completar este tutorial, debe tener instalado Visual Studio y la propiedad opcional **desarrollo de escritorio con C++** carga de trabajo o las herramientas de línea de comandos de compilación de Visual Studio.

Visual Studio es un entorno de desarrollo integrado (IDE) que admite un editor completo, los administradores de recursos, depuradores y los compiladores para numerosos lenguajes y plataformas. Para obtener información sobre cómo descargar e instalar Visual Studio, incluida la edición gratuita de Visual Studio Community y para incluir compatibilidad para el desarrollo de C o C++, vea [compatibilidad Install C++ en Visual Studio](../build/vscpp-step-0-installation.md).

Build Tools para Visual Studio instala los compiladores de línea de comandos, herramientas y las bibliotecas que necesita para compilar programas de C y C++. Es perfecto para laboratorios de compilación o aula ejercita e instala de forma relativamente rápida. Para instalar sólo las herramientas de línea de comandos, descargue [Build Tools para Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=875721).

Antes de generar un programa de C o C++ en la línea de comandos, debe comprobar que las herramientas están instaladas y que puede acceder a ellos desde la línea de comandos. Visual C++ tiene requisitos complejos para el entorno de línea de comandos encontrar las herramientas, encabezados y bibliotecas que utiliza. **No se puede utilizar Visual C++ en una ventana del símbolo del sistema sin formato** sin tener que realizar algunos preparativos. Afortunadamente, Visual C++ instala accesos directos para iniciar un símbolo que tiene el entorno configurado para las compilaciones de línea de comandos. Lamentablemente, los nombres de los accesos directos del símbolo del sistema para desarrolladores y dónde están ubicados son diferentes en casi todas las versiones de Visual C++ y en diferentes versiones de Windows. La primera tarea del tutorial es encontrar una válida para usar.

> [!NOTE]
> Un acceso directo del símbolo para desarrolladores establece automáticamente las rutas de acceso correctas para el compilador y las herramientas y para los encabezados necesarios y las bibliotecas. Deben establecer estos valores de entorno si usas normal **símbolo** ventana. Para obtener más información, consulte [establecer la ruta de acceso y las Variables de entorno para compilaciones de línea de comandos](../build/setting-the-path-and-environment-variables-for-command-line-builds.md). Se recomienda que usar un acceso directo del símbolo para desarrolladores en lugar de crear el suyo propio.

### <a name="open-a-developer-command-prompt"></a>Abra un símbolo del sistema para desarrolladores

1. Si ha instalado Visual Studio 2017 en Windows 10, abra el menú Inicio y elija **todas las aplicaciones**. Desplácese hacia abajo y abra el **Visual Studio 2017** carpeta (no en la aplicación de Visual Studio 2017). Elija **símbolo del sistema para desarrolladores para VS 2017** para abrir la ventana de símbolo del sistema.

   Si ha instalado Microsoft Visual C++ Build Tools 2015 en Windows 10, abra el **iniciar** menú y elija **todas las aplicaciones**. Desplácese hacia abajo y abra el **Visual C++ Build Tools** carpeta. Elija **línea de comandos de herramientas nativo de Visual C++ 2015 x86** para abrir la ventana de símbolo del sistema.

   Si está usando una versión diferente de Visual Studio o ejecutan una versión diferente de Windows, busque en el menú Inicio o página de inicio de una carpeta de herramientas de Visual Studio que contenga un acceso directo del símbolo para desarrolladores. También puede usar la función de búsqueda de Windows para buscar "símbolo" y elija una que coincida con la versión instalada de Visual Studio. Use el método abreviado para abrir la ventana de símbolo del sistema.

1. A continuación, compruebe que la línea de comandos para desarrolladores de Visual C++ se ha configurado correctamente. En la ventana de símbolo del sistema, escriba `cl` y compruebe que el resultado es similar:

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   Puede haber diferencias en el directorio actual o números de versión, según la versión de Visual C++ y las actualizaciones instaladas. Si la salida anterior es similar a lo que ve, estará listo para compilar programas de C o C++ en la línea de comandos.

   > [!NOTE]
   > Si se produce un error, como "'cl' no se reconoce como un comando interno o externo, programa operable o archivo por lotes," error de C1034 o LNK1104 al ejecutar el **cl** de comandos, o bien no está usando un símbolo del sistema, o algo va mal con la instalación de Visual C++. Debe corregir este problema antes de continuar.

   Si no se encuentra el programador acceso directo del símbolo del sistema, o si recibe un mensaje de error al escribir `cl`, a continuación, la instalación de Visual C++ puede tener un problema. Intente volver a instalar el componente de Visual C++ en Visual Studio, o volver a instalar Microsoft Visual C++ Build Tools. No vaya a la sección siguiente hasta que esto funcione. Para obtener más información sobre la instalación y solución de problemas de Visual C++, vea [instalar Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > Según la versión de Windows en el equipo y la configuración de seguridad del sistema, es posible que deba haga doble clic para abrir el menú contextual para el acceso de directo del símbolo del sistema para desarrolladores y, a continuación, elija **ejecutar como administrador** a compilar y ejecutar el programa que se crea siguiendo este tutorial correctamente.

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Crear un archivo de código fuente de Visual C++ y compilarlo en la línea de comandos

1. En la ventana de símbolo del sistema para desarrolladores, escriba `md c:\hello` para crear un directorio y, a continuación, escriba `cd c:\hello` para cambiar a ese directorio. Este directorio es donde se crean el archivo de origen y el programa compilado en.

1. Escriba `notepad hello.cpp` en la ventana de símbolo del sistema.

   Elija **Sí** cuando el Bloc de notas le pedirá que cree un archivo. Este paso abre una ventana del Bloc de notas en blanco, lista para escribir el código en un archivo denominado hello.cpp.

1. En el Bloc de notas, escriba las siguientes líneas de código:

   ```cpp
   #include <iostream>
   using namespace std;
   void main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   Este código es un programa sencillo que escribirá una línea de texto en la pantalla y, a continuación, salir. Para minimizar los errores, copie este código y péguelo en el Bloc de notas.

1. No olvide guardar su trabajo. En el Bloc de notas, en el menú **Archivo** , elija **Guardar**.

   Enhorabuena, ha creado un archivo de código fuente de Visual C++, hello.cpp, que está listo para compilar.

1. Cambie a la ventana de símbolo del sistema para desarrolladores. Escriba `dir` en el símbolo del sistema para mostrar el contenido del directorio c:\hello. Debería ver el hello.cpp del archivo de origen en la lista de directorios, que se parece algo como:

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

   Las fechas y otros detalles variarán en su equipo. Si no ve el archivo de código fuente, hello.cpp, asegúrese de que ha cambiado en el directorio c:\hello que creó y, en el Bloc de notas, asegúrese de que guardó el archivo de código fuente en este directorio. Además, asegúrese de que ha guardado el código fuente con una extensión de nombre de archivo .cpp, no una extensión. txt.

1. En el símbolo del sistema, escriba `cl /EHsc hello.cpp` para compilar el programa.

   El compilador cl.exe genera un archivo .obj que contiene el código compilado y, luego, ejecuta el enlazador para crear un programa ejecutable llamado hello.exe. Este nombre aparece en las líneas de información de salida que muestra el compilador. La salida del compilador debe ser similar:

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
   > Si se produce un error, como "'cl' no se reconoce como un comando interno o externo, programa operable o archivo por lotes," error de C1034 o LNK1104, el símbolo del sistema para desarrolladores no está configurado correctamente. Para obtener información sobre cómo solucionar este problema, vuelva a la **abra un símbolo del sistema para desarrolladores** sección.

   > [!NOTE]
   > Si se produce una advertencia o error del vinculador o compilador diferentes, revise el código fuente para corregir los errores, a continuación, guárdelo y vuelva a ejecutar el compilador. Para obtener información sobre los errores específicos, use el cuadro de búsqueda en esta página MSDN para buscar el número de error.

7. Para ejecutar el programa hello.exe, en el símbolo del sistema, escriba `hello`.

   El programa mostrará este texto y se cerrará:

   ```Output
   Hello, world, from Visual C++!
   ```

   Enhorabuena, acaba de compilar y ejecutar un programa de C++ con las herramientas de línea de comandos.

## <a name="next-steps"></a>Pasos siguientes

Es tan sencillo como un programa de C++ puede obtener este ejemplo "Hello, World". Programas del mundo real tienen archivos de encabezado y más archivos de código fuente, vincular en bibliotecas, y realizar trabajo útil.

Puede usar los pasos de este tutorial para crear su propio código de C++ en lugar de escribir el código de ejemplo que se muestra. También puede crear muchos programas de ejemplo de código de C++ que encuentre en otro lugar. Puede colocar el código fuente y compilar las aplicaciones en cualquier directorio de escritura. De forma predeterminada, el IDE de Visual Studio crea proyectos en la carpeta documentos en una subcarpeta de proyectos de una carpeta de Visual Studio con nombre para la versión de Visual Studio.

Para compilar un programa que tiene archivos de código fuente adicionales, escríbalos en la línea de comandos, como:

`cl /EHsc file1.cpp file2.cpp file3.cpp`

La opción de línea de comandos `/EHsc` indica al compilador que habilite el control de excepciones de C++. Para obtener más información, consulte [/EH (Modelo de control de excepciones)](../build/reference/eh-exception-handling-model.md).

Cuando se proporcionan más archivos de origen, el compilador usa el primer archivo de entrada para crear el nombre del programa. En este caso, genera un programa llamado file1.exe. Para cambiar el nombre a program1.exe, agregue un [/out](../build/reference/out-output-file-name.md) opción del vinculador:

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Y para detectar errores de programación más automáticamente, se recomienda compilar mediante el uso del [/w3](../build/reference/compiler-option-warning-level.md) o [/W4](../build/reference/compiler-option-warning-level.md) opción de nivel de advertencia:

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

El compilador, cl.exe, tiene muchas más opciones que puede aplicar para crear, optimizar, depurar y analizar el código. Para obtener una lista rápida, escriba `cl /?` en el símbolo del sistema de desarrollador. También puede compilar y vincular por separado y aplicar las opciones del vinculador en escenarios más complejos de compilación. Para obtener más información sobre el compilador y las opciones del vinculador y uso, consulte [C/C ++ Building Reference](../build/reference/c-cpp-building-reference.md).

Puede usar NMAKE y archivos MAKE o archivos de proyecto y MSBuild para configurar y compilar los proyectos más complejos en la línea de comandos. Para obtener más información sobre el uso de estas herramientas, consulte [referencia de NMAKE](../build/nmake-reference.md) y [MSBuild](../build/msbuild-visual-cpp.md).

Los lenguajes C y C++ son similares, pero no es el mismo. El compilador de Visual C++ usa una regla sencilla para determinar el idioma que desea utilizar cuando se compila el código. De forma predeterminada, el compilador de Visual C++ trata todos los archivos que finalizan en .c como código fuente de C, y todos los archivos que finalizan en .cpp como código fuente de C++. Para forzar al compilador que trate todos los archivos como C++ no dependientes en la extensión de nombre de archivo, use el [/TC](../build/reference/tc-tp-tc-tp-specify-source-file-type.md) opción del compilador.

El compilador de Visual C++ incluye una biblioteca de tiempo de ejecución de C (CRT) que es compatible con el estándar ISO C99, pero no es totalmente compatible. En la mayoría de los casos, código portable compilará y ejecutará según lo previsto. Visual C++ no admite algunos de los cambios de CRT en ISO C11. Ciertas funciones de biblioteca y los nombres de función POSIX están en desuso por el compilador de Visual C++. Se admiten las funciones, pero han cambiado los nombres preferidos. Para obtener más información, consulte [características de seguridad de CRT](../c-runtime-library/security-features-in-the-crt.md) y [advertencia del compilador (nivel 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Compilación de programas de C/C++](../build/building-c-cpp-programs.md)<br/>
[Opciones del compilador](../build/reference/compiler-options.md)
