---
title: 'Tutorial: compilar un programa de C en la línea de comandos'
ms.custom: conceptual
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
ms.openlocfilehash: 1b4e7f0f188ce7b3003f12cb7acafaf15a03d86a
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078251"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>Tutorial: compilar un programa de C en la línea de comandos

Visual C++ incluye un compilador de C que puede usar para crear todo desde programas de consola básicos hasta aplicaciones de escritorio de Windows completas, aplicaciones móviles, etc.

En este tutorial se muestra cómo crear un programa de C de estilo "Hello, World" básico mediante un editor de texto y, a continuación, compilarlo en la línea de comandos. Si prefiere trabajar con C++ en la línea de comandos, vea [Tutorial: compilar un C++ programa nativo en la línea de comandos](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md). Si desea probar el IDE de Visual Studio en lugar de usar la línea de comandos, vea [Tutorial: trabajar con proyectos y soluciones (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) o [usar el IDE de Visual Studio para C++ el desarrollo de escritorio](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="prerequisites"></a>Prerequisites

Para completar este tutorial, debe haber instalado Visual Studio y los componentes visuales C++ opcionales, o las herramientas de compilación para Visual Studio.

Visual Studio es un eficaz entorno de desarrollo integrado que admite un editor completo, administradores de recursos, depuradores y compiladores para varios lenguajes y plataformas. Para obtener información sobre estas características y cómo descargar e instalar Visual Studio, incluida la edición gratuita de Visual Studio Community, vea [instalar Visual Studio](/visualstudio/install/install-visual-studio).

La versión de herramientas de compilación para Visual Studio de Visual Studio instala solo el conjunto de herramientas de línea de comandos, los compiladores, las herramientas y las bibliotecas que C++ necesita para compilar C y programas. Es perfecta para laboratorios de compilación o ejercicios de la clase y se instala con relativamente rapidez. Para instalar solo el conjunto de herramientas de línea de comandos, descargue las herramientas de compilación para Visual Studio desde la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) y ejecute el instalador. En el instalador de Visual Studio, seleccione **C++** la carga de trabajo herramientas de compilación y elija **instalar**.

Antes de poder compilar un C++ programa de C o en la línea de comandos, debe comprobar que las herramientas están instaladas y que puede tener acceso a ellas desde la línea de comandos. Visual C++ tiene requisitos complejos para que el entorno de línea de comandos busque las herramientas, los encabezados y las bibliotecas que usa. **No se puede usar C++ visual en una ventana de símbolo del sistema** sin necesidad de preparación. Necesita una ventana de símbolo del *sistema para desarrolladores* , que es una ventana de símbolo del sistema normal que tiene establecidas todas las variables de entorno necesarias. Afortunadamente, visual C++ instala accesos directos para que pueda iniciar símbolos del sistema para desarrolladores que tengan el entorno configurado para las compilaciones de línea de comandos. Desafortunadamente, los nombres de los accesos directos del símbolo del sistema para desarrolladores y dónde se encuentran son diferentes en casi todas C++ las versiones de visual y en versiones diferentes de Windows. La primera tarea del tutorial es encontrar el acceso directo adecuado para su uso.

> [!NOTE]
> Un acceso directo del símbolo del sistema para desarrolladores establece automáticamente las rutas de acceso correctas para el compilador y las herramientas, y para los encabezados y bibliotecas necesarios. Algunos de estos valores son diferentes para cada configuración de compilación. Debe establecer estos valores de entorno usted mismo si no usa uno de los métodos abreviados. Para más información, vea [Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](setting-the-path-and-environment-variables-for-command-line-builds.md). Dado que el entorno de compilación es complejo, se recomienda encarecidamente usar un acceso directo del símbolo del sistema para desarrolladores en lugar de crear el suyo propio.

Estas instrucciones varían en función de la versión de Visual Studio que se use. Antes de continuar, asegúrese de que el selector de versión en la parte superior izquierda de esta página esté configurado correctamente.

::: moniker range="vs-2019"

## <a name="open-a-developer-command-prompt-in-visual-studio-2019"></a>Abra un símbolo del sistema para desarrolladores en Visual Studio 2019

Si ha instalado Visual Studio 2019 en Windows 10, abra el menú Inicio y, a continuación, desplácese hacia abajo y abra la carpeta **visual studio 2019** (no la aplicación de visual Studio 2019). Elija **símbolo del sistema para desarrolladores para VS 2019** para abrir la ventana del símbolo del sistema.

Si usa una versión diferente de Windows, busque en el menú Inicio o en la página de inicio una carpeta de Visual Studio Tools que contenga un acceso directo del símbolo del sistema para desarrolladores. También puede usar la función de búsqueda de Windows para buscar "símbolo del sistema para desarrolladores" y elegir uno que coincida con la versión instalada de Visual Studio. Use el acceso directo para abrir la ventana del símbolo del sistema.

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-developer-command-prompt-in-visual-studio-2017"></a>Abra un símbolo del sistema para desarrolladores en Visual Studio 2017

Si ha instalado Visual Studio 2017 en Windows 10, abra el menú Inicio y, a continuación, desplácese hacia abajo y abra la carpeta **visual studio 2017** (no la aplicación de visual Studio 2017). Elija **símbolo del sistema para desarrolladores para VS 2017** para abrir la ventana del símbolo del sistema.

Si está ejecutando una versión diferente de Windows, busque en el menú Inicio o en la página de inicio una carpeta de Visual Studio Tools que contenga un acceso directo del símbolo del sistema para desarrolladores. También puede usar la función de búsqueda de Windows para buscar "símbolo del sistema para desarrolladores" y elegir uno que coincida con la versión instalada de Visual Studio. Use el acceso directo para abrir la ventana del símbolo del sistema.

::: moniker-end

::: moniker range="vs-2015"

## <a name="open-a-developer-command-prompt-in-visual-studio-2015"></a>Abra un símbolo del sistema para desarrolladores en Visual Studio 2015

Si ha instalado Microsoft Visual C++ Build Tools 2015 en Windows 10, abra el menú **Inicio** y, a continuación, desplácese hacia abajo y abra la carpeta **Visual C++ build tools** . Elija **Visual C++ 2015 símbolo del sistema de las herramientas nativas x86** para abrir la ventana del símbolo del sistema.

Si está ejecutando una versión diferente de Windows, busque en el menú Inicio o en la página de inicio una carpeta de Visual Studio Tools que contenga un acceso directo del símbolo del sistema para desarrolladores. También puede usar la función de búsqueda de Windows para buscar "símbolo del sistema para desarrolladores" y elegir uno que coincida con la versión instalada de Visual Studio. Use el acceso directo para abrir la ventana del símbolo del sistema.

::: moniker-end

A continuación, compruebe que el C++ símbolo del sistema para desarrolladores de Visual está configurado correctamente. En la ventana del símbolo del sistema, escriba `cl` y compruebe que la salida es similar a la siguiente:

```Output
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

usage: cl [ option... ] filename... [ /link linkoption... ]
```

Puede haber diferencias en el directorio actual o en los números de versión, en función de la versión C++ de visual y de las actualizaciones instaladas. Si la salida anterior es similar a lo que ve, está listo para compilar C o C++ programas en la línea de comandos.

> [!NOTE]
> Si recibe un error como "CL" no se reconoce como un comando interno o externo, un programa o archivo por lotes ejecutable, "error C1034 o error LNK1104 al ejecutar el comando **cl** , no está usando un símbolo del sistema para desarrolladores o hay algún problema con la instalación de Visual C++. Debe corregir este problema para poder continuar.

Si no encuentra el acceso directo del símbolo del sistema para desarrolladores, o si recibe un mensaje de error al escribir `cl`, es C++ posible que la instalación de Visual tenga un problema. Si usa Visual Studio 2017 o una versión posterior, intente volver a instalar el **desarrollo de escritorio C++ con** carga de trabajo en el instalador de Visual Studio. Para obtener más información, consulte [instalación C++ de la compatibilidad en Visual Studio](vscpp-step-0-installation.md). O bien, vuelva a instalar las herramientas de compilación desde la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/) . No vaya a la sección siguiente hasta que esto funcione. Para obtener más información sobre la instalación y solución de problemas de Visual Studio, vea [instalar Visual Studio](/visualstudio/install/install-visual-studio).

> [!NOTE]
> Dependiendo de la versión de Windows del equipo y la configuración de seguridad del sistema, es posible que tenga que hacer clic con el botón secundario para abrir el menú contextual del acceso directo del símbolo del sistema para desarrolladores y, a continuación, elegir **Ejecutar como administrador** para compilar y ejecutar correctamente el programa que cree siguiendo este tutorial.

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>Crear un archivo de código fuente de C y compilarlo en la línea de comandos

1. En la ventana del símbolo del sistema para desarrolladores, escriba `cd c:\` para cambiar el directorio de trabajo actual a la raíz de la unidad C:. Después, escriba `md c:\simple` para crear un directorio y, a continuación, escriba `cd c:\simple` para cambiar a ese directorio. Este directorio contendrá el archivo de código fuente y el programa compilado.

1. Escriba `notepad simple.c` en el símbolo del sistema para desarrolladores. En el cuadro de diálogo de alerta del Bloc de notas que aparece, elija **sí** para crear un nuevo archivo. c simple en el directorio de trabajo.

1. En el Bloc de notas, escriba las líneas de código siguientes:

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. En la barra de menús del Bloc de notas, elija **archivo** > **Guardar** para guardar simple. c en el directorio de trabajo.

1. Vuelva a la ventana del símbolo del sistema para desarrolladores. Escriba `dir` en el símbolo del sistema para mostrar el contenido del directorio c:\simple. Debería ver el archivo de código fuente simple. c en la lista de directorios, que tiene un aspecto similar al siguiente:

    ```Output
    C:\simple>dir
     Volume in drive C has no label.
     Volume Serial Number is CC62-6545

     Directory of C:\simple

    10/02/2017  03:46 PM    <DIR>          .
    10/02/2017  03:46 PM    <DIR>          ..
    10/02/2017  03:36 PM               143 simple.c
                   1 File(s)            143 bytes
                   2 Dir(s)  514,900,566,016 bytes free

    ```

   Las fechas y otros detalles variarán en el equipo. Si no ve el archivo de código fuente, simple. c, asegúrese de que ha cambiado al directorio c:\simple que ha creado y, en el Bloc de notas, asegúrese de que ha guardado el archivo de código fuente en este directorio. Asegúrese también de que ha guardado el código fuente con una extensión de nombre de archivo. c, no una extensión. txt.

1. Para compilar el programa, escriba `cl simple.c` en el símbolo del sistema para desarrolladores.

   Puede ver el nombre del programa ejecutable, simple. exe, en las líneas de información de salida que muestra el compilador:

    ```Output
    c:\simple>cl simple.c
    Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
    Copyright (C) Microsoft Corporation.  All rights reserved.

    simple.c
    Microsoft (R) Incremental Linker Version 14.10.25017.0
    Copyright (C) Microsoft Corporation.  All rights reserved.

    /out:simple.exe
    simple.obj
    ```

   > [!NOTE]
   > Si recibe un error como "CL" no se reconoce como un comando interno o externo, un programa o archivo por lotes ejecutable, "error C1034 o error LNK1104, el símbolo del sistema para desarrolladores no está configurado correctamente. Para obtener información acerca de cómo corregir este problema, vuelva a la sección **abrir un símbolo del sistema para desarrolladores** .

   > [!NOTE]
   > Si obtiene un error o una advertencia del compilador o vinculador diferente, revise el código fuente para corregir los errores y, a continuación, guárdelo y vuelva a ejecutar el compilador. Para obtener información sobre errores específicos, utilice el cuadro de búsqueda de la parte superior de esta página para buscar el número de error.

1. Para ejecutar el programa, escriba `simple` en el símbolo del sistema.

   El programa muestra este texto y, a continuación, se cierra:

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   Enhorabuena, ha compilado y ejecutado un programa de C mediante la línea de comandos.

## <a name="next-steps"></a>Pasos siguientes

Este ejemplo "Hello, World" es tan sencillo como el que puede obtener un programa de C. Los programas del mundo real tienen archivos de encabezado y más archivos de código fuente, vínculos en bibliotecas y trabajo útil.

Puede usar los pasos de este tutorial para compilar su propio código de C en lugar de escribir el código de ejemplo que se muestra. También puede compilar muchos programas de ejemplo de código de C que encuentre en otro lugar. Para compilar un programa que tiene archivos de código fuente adicionales, escríbalos todos en la línea de comandos, como:

`cl file1.c file2.c file3.c`

El compilador genera un programa llamado archivo1. exe. Para cambiar el nombre a Program1. exe, agregue una opción [/out](reference/out-output-file-name.md) del enlazador:

`cl file1.c file2.c file3.c /link /out:program1.exe`

Y para detectar más errores de programación automáticamente, se recomienda compilar mediante la opción de nivel de advertencia [/W3](reference/compiler-option-warning-level.md) o [/W4](reference/compiler-option-warning-level.md) :

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

El compilador, cl. exe, tiene muchas más opciones que se pueden aplicar para compilar, optimizar, depurar y analizar el código. Para obtener una lista rápida, escriba `cl /?` en el símbolo del sistema para desarrolladores. También puede compilar y vincular por separado y aplicar las opciones del enlazador en escenarios de compilación más complejos. Para obtener más información sobre las opciones del compilador y del vinculador y el uso, vea [C/C++ Building Reference](reference/c-cpp-building-reference.md).

Puede usar NMAKE y archivos make, o MSBuild y archivos de proyecto para configurar y compilar proyectos más complejos en la línea de comandos. Para obtener más información sobre el uso de estas herramientas, vea [referencia de NMAKE](reference/nmake-reference.md) y [msbuild](msbuild-visual-cpp.md).

Los lenguajes C++ C y son similares, pero no los mismos. El compiladorC++ de Microsoft C/(MSVC) usa una regla simple para determinar qué lenguaje usar al compilar el código. De forma predeterminada, el compilador MSVC trata todos los archivos que finalizan en. c como código fuente de C y todos los archivos C++ que finalizan en. cpp como código fuente. Para forzar al compilador a tratar todos los archivos como valores de C que no dependen de la extensión de nombre de archivo, use la opción del compilador [/TC](reference/tc-tp-tc-tp-specify-source-file-type.md) .

MSVC es compatible con el estándar ISO C99, pero no es totalmente compatible. En la mayoría de los casos, el código C portátil se compilará y se ejecutará según lo previsto. Visual C++ no es compatible con la mayoría de los cambios en ISO C11. Ciertas funciones de biblioteca y nombres de función POSIX están en desuso en MSVC. Se admiten las funciones, pero los nombres preferidos han cambiado. Para obtener más información, vea [características de seguridad en CRT](../c-runtime-library/security-features-in-the-crt.md) y [Advertencia del compilador (nivel 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Consulte también

[Tutorial: Crear un programa de C++ estándar (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[Referencia del lenguaje C](../c-language/c-language-reference.md)<br/>
[Proyectos y sistemas de compilación](projects-and-build-systems-cpp.md)<br/>
[Compatibilidad](../c-runtime-library/compatibility.md)
