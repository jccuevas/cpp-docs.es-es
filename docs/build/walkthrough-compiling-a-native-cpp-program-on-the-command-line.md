---
title: 'Tutorial: Compilar C++ un programa nativo en la línea de comandos'
description: Use el compilador de Microsoft C++ desde un símbolo del sistema.
ms.custom: conceptual
ms.date: 04/23/2019
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
ms.openlocfilehash: 36017b28ab91478da2515cd7c8588a998013171d
ms.sourcegitcommit: c53a3efcc5d51fc55fa57ac83cca796b33ae888f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71960712"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>Tutorial: Compilar C++ un programa nativo en la línea de comandos

Visual Studio incluye un compilador C++ de línea de comandos que puede usar para crear todo desde aplicaciones de consola básicas hasta plataforma universal de Windows aplicaciones, aplicaciones de escritorio, controladores de dispositivos y componentes de .net.

En este tutorial, creará un programa básico de estilo C++ "Hello, World" con un editor de texto y, a continuación, lo compilará en la línea de comandos. Si desea probar el IDE de Visual Studio en lugar de usar la línea de comandos, vea [Walkthrough: Trabajar con proyectos y soluciones (C++) ](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) o [usar el IDE de Visual Studio C++ para el desarrollo de escritorio](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

En este tutorial, puede usar su propio programa de Visual C++ en lugar de escribir el que se muestra o usar un código de ejemplo de Visual C++ de otro artículo de ayuda.

## <a name="prerequisites"></a>Requisitos previos

Para completar este tutorial, debe tener instalado Visual Studio y el **desarrollo de escritorio opcional con C++**  carga de trabajo, o las herramientas de compilación de línea de comandos para Visual Studio.

Visual Studio es un eficaz entorno de desarrollo integrado (IDE) que admite un editor completo, administradores de recursos, depuradores y compiladores para varios lenguajes y plataformas. Para obtener información sobre cómo descargar e instalar Visual Studio, incluida la edición gratuita de Visual Studio Community, y para incluir compatibilidad con CC++ /Development, [consulte C++ instalación de la compatibilidad en Visual Studio](vscpp-step-0-installation.md).

Las herramientas de compilación para Visual Studio solo instalan los compiladores de línea de comandos, las herramientas y las bibliotecas que necesita para C++ compilar C y programas. Es perfecta para laboratorios de compilación o ejercicios de la clase y se instala con relativamente rapidez. Para instalar solo las herramientas de línea de comandos, busque herramientas de compilación para Visual Studio en la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/) .

Antes de poder compilar un C++ programa de C o en la línea de comandos, debe comprobar que las herramientas están instaladas y que puede tener acceso a ellas desde la línea de comandos. Visual C++ tiene requisitos complejos para que el entorno de línea de comandos busque las herramientas, los encabezados y las bibliotecas que usa. **No se puede usar C++ visual en una ventana del símbolo del sistema** sin necesidad de realizar ninguna preparación. Afortunadamente, visual C++ instala accesos directos para que pueda iniciar un símbolo del sistema para desarrolladores que tenga el entorno configurado para las compilaciones de línea de comandos. Desafortunadamente, los nombres de los accesos directos del símbolo del sistema para desarrolladores y dónde se encuentran son diferentes en casi todas C++ las versiones de visual y en versiones diferentes de Windows. La primera tarea del tutorial es encontrar la que se va a usar.

> [!NOTE]
> Un acceso directo del símbolo del sistema para desarrolladores establece automáticamente las rutas de acceso correctas para el compilador y las herramientas, y para los encabezados y bibliotecas necesarios. Debe establecer estos valores de entorno manualmente si usa una ventana de **símbolo del sistema** normal. Para más información, vea [Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](setting-the-path-and-environment-variables-for-command-line-builds.md). Se recomienda usar un acceso directo del símbolo del sistema para desarrolladores en lugar de crear el suyo propio.

### <a name="open-a-developer-command-prompt"></a>Abra un símbolo del sistema para desarrolladores

1. Si ha instalado Visual Studio 2017 o una versión posterior en Windows 10, abra el menú Inicio y elija **todas las aplicaciones**. Desplácese hacia abajo y abra la carpeta **Visual Studio** (no la aplicación de Visual Studio). Elija **símbolo del sistema para desarrolladores para vs** para abrir la ventana del símbolo del sistema.

   Si ha instalado Microsoft Visual C++ Build Tools 2015 en Windows 10, abra el menú **Inicio** y elija **todas las aplicaciones**. Desplácese hacia abajo y abra la carpeta  **C++ visual build tools** . Elija **Visual C++ 2015 símbolo del sistema de las herramientas nativas x86** para abrir la ventana del símbolo del sistema.

   También puede usar la función de búsqueda de Windows para buscar "símbolo del sistema para desarrolladores" y elegir uno que coincida con la versión instalada de Visual Studio. Use el acceso directo para abrir la ventana del símbolo del sistema.

1. A continuación, compruebe que el C++ símbolo del sistema para desarrolladores de Visual está configurado correctamente. En la ventana del símbolo del sistema, escriba `cl` y compruebe que la salida es similar a la siguiente:

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   Puede haber diferencias en el directorio actual o en los números de versión, en función de la versión C++ de visual y de las actualizaciones instaladas. Si la salida anterior es similar a lo que ve, está listo para compilar C o C++ programas en la línea de comandos.

   > [!NOTE]
   > Si recibe un error como "CL" no se reconoce como un comando interno o externo, un programa o archivo por lotes ejecutable, "error C1034 o error LNK1104 al ejecutar el comando **cl** , no está usando un símbolo del sistema para desarrolladores o hay algún problema con la instalación de Visual C++. Debe corregir este problema para poder continuar.

   Si no encuentra el acceso directo del símbolo del sistema para desarrolladores, o si recibe un mensaje de error al especificar `cl`, puede C++ que la instalación de Visual tenga un problema. Intente volver a instalar el componente C++ visual en Visual Studio o vuelva a instalar las herramientas de C++ compilación de Microsoft Visual. No vaya a la sección siguiente hasta que esto funcione. Para obtener más información sobre la instalación y solución C++de problemas de Visual, vea [instalar Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > Dependiendo de la versión de Windows del equipo y la configuración de seguridad del sistema, es posible que tenga que hacer clic con el botón derecho para abrir el menú contextual del acceso directo del símbolo del sistema para desarrolladores y, a continuación, elegir **Ejecutar como administrador** para compilar y ejecutar correctamente el programa que se crea siguiendo este tutorial.

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Crear un archivo C++ de código fuente visual y compilarlo en la línea de comandos

1. En la ventana del símbolo del sistema para desarrolladores, escriba `md c:\hello` para crear un directorio y, a continuación, escriba `cd c:\hello` para cambiar a ese directorio. Este directorio es donde se crean el archivo de código fuente y el programa compilado en.

1. Escriba `notepad hello.cpp` en la ventana del símbolo del sistema.

   Elija **sí** cuando el Bloc de notas le pida que cree un archivo. Este paso abre una ventana en blanco del Bloc de notas, lista para que escriba el código en un archivo denominado Hello. cpp.

1. En el Bloc de notas, escriba las líneas de código siguientes:

   ```cpp
   #include <iostream>
   using namespace std;
   void main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   Este código es un programa sencillo que escribirá una línea de texto en la pantalla y, a continuación, se cerrará. Para minimizar los errores, copie este código y péguelo en el Bloc de notas.

1. No olvide guardar su trabajo. En el Bloc de notas, en el menú **Archivo** , elija **Guardar**.

   Enhorabuena, ha creado un C++ archivo de código fuente, Hello. cpp, que está listo para compilar.

1. Vuelva a la ventana del símbolo del sistema para desarrolladores. Escriba `dir` en el símbolo del sistema para mostrar el contenido del directorio c:\hello. Debería ver el archivo de código fuente Hello. cpp en la lista de directorios, que tiene un aspecto similar al siguiente:

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

   Las fechas y otros detalles variarán en el equipo. Si no ve el archivo de código fuente, Hello. cpp, asegúrese de que ha cambiado al directorio c:\hello que ha creado y, en el Bloc de notas, asegúrese de que ha guardado el archivo de código fuente en este directorio. Asegúrese también de que ha guardado el código fuente con una extensión de nombre de archivo. cpp, no una extensión. txt.

1. En el símbolo del sistema para desarrolladores, escriba `cl /EHsc hello.cpp` para compilar el programa.

   El compilador cl.exe genera un archivo .obj que contiene el código compilado y, luego, ejecuta el enlazador para crear un programa ejecutable llamado hello.exe. Este nombre aparece en las líneas de información de salida que muestra el compilador. La salida del compilador debe tener un aspecto similar al siguiente:

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
   > Si recibe un error como "CL" no se reconoce como un comando interno o externo, un programa o archivo por lotes ejecutable, "error C1034 o error LNK1104, el símbolo del sistema para desarrolladores no está configurado correctamente. Para obtener información acerca de cómo corregir este problema, vuelva a la sección **abrir un símbolo del sistema para desarrolladores** .

   > [!NOTE]
   > Si obtiene un error o una advertencia del compilador o vinculador diferente, revise el código fuente para corregir los errores y, a continuación, guárdelo y vuelva a ejecutar el compilador. Para obtener información acerca de los errores específicos, utilice el cuadro de búsqueda de esta página de MSDN para buscar el número de error.

1. Para ejecutar el programa hello.exe, en el símbolo del sistema, escriba `hello`.

   El programa mostrará este texto y se cerrará:

   ```Output
   Hello, world, from Visual C++!
   ```

   Enhorabuena, ha compilado y ejecutado un C++ programa con las herramientas de línea de comandos.

## <a name="next-steps"></a>Pasos siguientes

Este ejemplo "Hello, World" es tan sencillo como puede obtener C++ un programa. Los programas del mundo real tienen archivos de encabezado y más archivos de código fuente, vínculos en bibliotecas y trabajo útil.

Puede usar los pasos de este tutorial para crear su propio C++ código en lugar de escribir el código de ejemplo que se muestra. También puede compilar C++ muchos programas de ejemplo de código que encuentre en otra parte. Puede colocar el código fuente y compilar las aplicaciones en cualquier directorio grabable. De forma predeterminada, el IDE de Visual Studio crea proyectos en la carpeta de documentos, en una subcarpeta de proyectos de una carpeta de Visual Studio denominada para su versión de Visual Studio.

Para compilar un programa que tiene archivos de código fuente adicionales, escríbalos todos en la línea de comandos, como:

`cl /EHsc file1.cpp file2.cpp file3.cpp`

La opción de línea de comandos `/EHsc` indica al compilador que habilite el control de excepciones de C++. Para obtener más información, consulte [/EH (Modelo de control de excepciones)](reference/eh-exception-handling-model.md).

Cuando se suministran archivos de código fuente adicionales, el compilador usa el primer archivo de entrada para crear el nombre del programa. En este caso, genera un programa llamado archivo1. exe. Para cambiar el nombre a Program1. exe, agregue una opción [/out](reference/out-output-file-name.md) del enlazador:

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Y para detectar más errores de programación automáticamente, se recomienda compilar mediante la opción de nivel de advertencia [/W3](reference/compiler-option-warning-level.md) o [/W4](reference/compiler-option-warning-level.md) :

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

El compilador, cl. exe, tiene muchas más opciones que se pueden aplicar para compilar, optimizar, depurar y analizar el código. Para obtener una lista rápida, escriba `cl /?` en el símbolo del sistema para desarrolladores. También puede compilar y vincular por separado y aplicar las opciones del enlazador en escenarios de compilación más complejos. Para obtener más información sobre las opciones del compilador y del vinculador y el uso, vea [C/C++ Building Reference](reference/c-cpp-building-reference.md).

Puede usar NMAKE y archivos make, o MSBuild y archivos de proyecto para configurar y compilar proyectos más complejos en la línea de comandos. Para obtener más información sobre el uso de estas herramientas, vea [referencia de NMAKE](reference/nmake-reference.md) y [msbuild](msbuild-visual-cpp.md).

Los lenguajes C++ C y son similares, pero no los mismos. El compilador MSVC usa una regla simple para determinar qué lenguaje usar al compilar el código. De forma predeterminada, el compilador MSVC trata todos los archivos que finalizan en. c como código fuente de C y todos los archivos C++ que finalizan en. cpp como código fuente. Para forzar al compilador a tratar C++ todos los archivos como no dependientes de la extensión de nombre de archivo, use la opción del compilador [/TP](reference/tc-tp-tc-tp-specify-source-file-type.md) .

El compilador MSVC incluye una biblioteca en tiempo de ejecución de C (CRT) que es compatible con el estándar ISO C99, pero no es estrictamente compatible. En la mayoría de los casos, el código portable se compilará y se ejecutará según lo previsto. Visual C++ no admite algunos de los cambios de CRT en ISO C11. Ciertas funciones de biblioteca y nombres de función POSIX están en desuso en el compilador MSVC. Se admiten las funciones, pero los nombres preferidos han cambiado. Para obtener más información, vea [características de seguridad en CRT](../c-runtime-library/security-features-in-the-crt.md) y [Advertencia del compilador (nivel 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Proyectos y sistemas de compilación](projects-and-build-systems-cpp.md)<br/>
[Opciones del compilador de MSVC](reference/compiler-options.md)
