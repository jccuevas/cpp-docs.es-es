---
title: 'Tutorial: Compilar un programa de C en la línea de comandos'
ms.custom: conceptual
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
ms.openlocfilehash: d807fa75b32b515c2222fec9ea9d070266303e33
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335262"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>Tutorial: Compilar un programa de C en la línea de comandos

Visual C++ incluye un compilador de C que puede usar para crear desde programas básicos de la consola hasta aplicaciones de escritorio de Windows completas, aplicaciones móviles y mucho más.

En este tutorial, aprenderá a crear un programa de consola de C básico de estilo "Hola mundo" con un editor de texto y, luego, lo compilará en la línea de comandos. Si prefiere trabajar en C++ en la línea de comandos, consulte [Tutorial: Compilar un programa nativo de C++ en la línea de comandos](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md). Si quiere probar el IDE de Visual Studio en lugar de usar la línea de comandos, vea [Tutorial: Trabajar con proyectos y soluciones (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) o [Usar el IDE de Visual Studio para desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="prerequisites"></a>Requisitos previos

Para completar este tutorial, debe haber instalado Visual Studio y los componentes de Visual C++ opcionales, o bien Build Tools para Visual Studio.

Visual Studio es un eficaz entorno de desarrollo integrado que admite un editor con funciones completas, administradores de recursos, depuradores y compiladores para varios lenguajes y plataformas. Para obtener información sobre estas características y cómo descargar e instalar Visual Studio, incluida la edición gratuita de Visual Studio Community, consulte [Instalar Visual Studio](/visualstudio/install/install-visual-studio).

La versión de Build Tools para Visual Studio solo instala el conjunto de herramientas de línea de comandos, los compiladores, las herramientas y las bibliotecas que necesita para compilar programas de C y C++. Resulta perfecta para laboratorios de compilación o ejercicios en aulas, y se instala con relativa rapidez. Para instalar solo las herramientas de línea de comandos, descargue Build Tools para Visual Studio en la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) y ejecute el instalador. En el instalador de Visual Studio, seleccione la carga de trabajo de las **herramientas de compilación de C++** y haga clic en **Instalar**.

Antes de compilar un programa de C o C++ en la línea de comandos, debe comprobar que las herramientas están instaladas y que puede acceder a ellas desde la línea de comandos. Visual C++ tiene requisitos complejos para que el entorno de línea de comandos busque las herramientas, los encabezados y las bibliotecas que usa. **No se puede usar Visual C++ en una ventana del símbolo del sistema sin formato** sin cierta preparación. Necesita una ventana del *símbolo del sistema para desarrolladores*, que es una ventana normal del símbolo del sistema que tiene configuradas todas las variables de entorno necesarias. Afortunadamente, Visual C++ instala accesos directos para que pueda iniciar símbolos del sistema para desarrolladores con el entorno configurado para compilaciones de línea de comandos. Desafortunadamente, los nombres de los accesos directos del símbolo del sistema para desarrolladores y dónde se encuentran son diferentes en casi todas las versiones de Visual C++ y en versiones diferentes de Windows. La primera tarea del tutorial consiste en encontrar el acceso directo adecuado que se va a usar.

> [!NOTE]
> Un acceso directo del símbolo del sistema para desarrolladores establece automáticamente las rutas de acceso correctas para el compilador y las herramientas, así como para los encabezados y bibliotecas necesarios. Algunos de estos valores son diferentes para cada configuración de compilación. Debe establecer por su cuenta estos valores de entorno si no usa uno de los accesos directos. Para más información, vea [Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](setting-the-path-and-environment-variables-for-command-line-builds.md). Dado que el entorno de compilación es complejo, se recomienda encarecidamente usar un acceso directo del símbolo del sistema para desarrolladores, en lugar de crear uno propio.

Estas instrucciones varían según la versión de Visual Studio que use. Para ver la documentación de su versión preferida de Visual Studio, use el control de selector **Versión**. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker range="vs-2019"

## <a name="open-a-developer-command-prompt-in-visual-studio-2019"></a>Apertura de un símbolo del sistema para desarrolladores en Visual Studio 2019

Si ha instalado Visual Studio 2019 en Windows 10, abra el menú Inicio, desplácese hacia abajo y abra la carpeta **Visual Studio 2019** (no la aplicación Visual Studio 2019). Elija **Símbolo del sistema para desarrolladores de VS 2019** para abrir la ventana del símbolo del sistema.

Si usa una versión diferente de Windows, busque en el menú Inicio o en la página de inicio una carpeta de herramientas de Visual Studio que contenga un acceso directo del símbolo del sistema para desarrolladores. También puede usar la función de búsqueda de Windows para buscar "símbolo del sistema para desarrolladores" y elegir uno que coincida con la versión instalada de Visual Studio. Use el acceso directo para abrir la ventana del símbolo del sistema.

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-developer-command-prompt-in-visual-studio-2017"></a>Apertura de un símbolo del sistema para desarrolladores en Visual Studio 2017

Si ha instalado Visual Studio 2017 en Windows 10, abra el menú Inicio, desplácese hacia abajo y abra la carpeta **Visual Studio 2017** (no la aplicación Visual Studio 2017). Elija **Símbolo del sistema para desarrolladores de VS 2017** para abrir la ventana del símbolo del sistema.

Si ejecuta una versión diferente de Windows, busque en el menú Inicio o en la página de inicio una carpeta de herramientas de Visual Studio que contenga un acceso directo del símbolo del sistema para desarrolladores. También puede usar la función de búsqueda de Windows para buscar "símbolo del sistema para desarrolladores" y elegir uno que coincida con la versión instalada de Visual Studio. Use el acceso directo para abrir la ventana del símbolo del sistema.

::: moniker-end

::: moniker range="vs-2015"

## <a name="open-a-developer-command-prompt-in-visual-studio-2015"></a>Apertura de un símbolo del sistema para desarrolladores en Visual Studio 2015

Si ha instalado Microsoft Visual C++ Build Tools 2015 en Windows 10, abra el menú **Inicio**, desplácese hacia abajo y abra la carpeta **Herramientas de compilación de Visual C++** . Elija **Símbolo del sistema de las herramientas nativas x86 de Visual C++ 2015** para abrir la ventana del símbolo del sistema.

Si ejecuta una versión diferente de Windows, busque en el menú Inicio o en la página de inicio una carpeta de herramientas de Visual Studio que contenga un acceso directo del símbolo del sistema para desarrolladores. También puede usar la función de búsqueda de Windows para buscar "símbolo del sistema para desarrolladores" y elegir uno que coincida con la versión instalada de Visual Studio. Use el acceso directo para abrir la ventana del símbolo del sistema.

::: moniker-end

Después, compruebe que el símbolo del sistema para desarrolladores de Visual C++ está configurado correctamente. En la ventana del símbolo del sistema, escriba `cl` y compruebe que la salida es similar a la siguiente:

```Output
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

usage: cl [ option... ] filename... [ /link linkoption... ]
```

Puede haber diferencias en el directorio o los números de versión actuales, en función de la versión de Visual C++ y de las actualizaciones instaladas. Si la salida anterior es similar a lo que ve, está listo para compilar programas de C o C++ en la línea de comandos.

> [!NOTE]
> Si recibe un error como "'cl' no se reconoce como un comando interno o externo, programa o archivo por lotes ejecutable", un error C1034 o un error LNK1104 al ejecutar el comando **cl**, significa que no usa un símbolo del sistema para desarrolladores o que hay algún problema con la instalación de Visual C++. Debe corregir este error para poder continuar.

Si no encuentra el acceso directo del símbolo del sistema para desarrolladores, o si recibe un mensaje de error al escribir `cl`, es posible que la instalación de Visual C++ tenga un problema. Si usa Visual Studio 2017 o una versión posterior, pruebe a instalar de nuevo la carga de trabajo **Desarrollo para el escritorio con C++** en el instalador de Visual Studio. Para obtener más información, consulte [Instalación de compatibilidad con C++ en Visual Studio](vscpp-step-0-installation.md). También puede volver a instalar Build Tools desde la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/). No pase a la sección siguiente hasta que funcione. Para obtener más información sobre cómo instalar y solucionar problemas de Visual Studio, vea [Instalación de Visual Studio](/visualstudio/install/install-visual-studio).

> [!NOTE]
> En función de la versión de Windows del equipo y de la configuración de seguridad del sistema, es posible que deba hacer clic con el botón derecho para abrir el menú contextual del acceso directo del símbolo del sistema para desarrolladores y, después, elegir **Ejecutar como administrador** para compilar y ejecutar correctamente el programa que se crea siguiendo este tutorial.

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>Creación de un archivo de código fuente de C y compilación en la línea de comandos

1. En la ventana del símbolo del sistema para desarrolladores, escriba `cd c:\` para cambiar el directorio de trabajo actual a la raíz de la unidad C:. Después, escriba `md c:\simple` para crear un directorio y `cd c:\simple` para cambiar a ese directorio. Este directorio contendrá el archivo de código fuente y el programa compilado.

1. Escriba `notepad simple.c` en el símbolo del sistema para desarrolladores. En el cuadro de diálogo de alerta del Bloc de notas que aparece, elija **Sí** para crear un archivo simple.c en el directorio de trabajo.

1. En el Bloc de notas, escriba las líneas de código siguientes:

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. En la barra de menús del Bloc de notas, elija **Archivo**  > **Guardar** para guardar simple.c en el directorio de trabajo.

1. Cambie a la ventana del símbolo del sistema para desarrolladores. Escriba `dir` en el símbolo del sistema para mostrar el contenido del directorio c:\simple. Debería ver el archivo de código fuente simple.c en la lista de directorios, con un aspecto similar al siguiente:

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

   Las fechas y otros detalles serán distintos en su equipo. Si no ve el archivo de código fuente simple.c, asegúrese de que ha cambiado al directorio c:\simple creado y, en el Bloc de notas, compruebe que ha guardado el archivo de código fuente en este directorio. Asegúrese también de que ha guardado el código fuente con una extensión de nombre de archivo .c, no con una extensión .txt.

1. Para compilar el programa, escriba `cl simple.c` en el símbolo del sistema para desarrolladores.

   Puede ver el nombre del programa ejecutable (simple.exe) en las líneas de información de salida que muestra el compilador:

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
   > Si obtiene un error como "'cl' no se reconoce como un comando interno o externo, programa o archivo por lotes ejecutable", un error C1034 o un error LNK1104, el símbolo del sistema para desarrolladores no está correctamente configurado. Para obtener información sobre cómo corregir este problema, vuelva a la sección **Apertura de un símbolo del sistema para desarrolladores**.

   > [!NOTE]
   > Si recibe otra advertencia o error del compilador o del enlazador, revise el código fuente para corregir los errores, guárdelo y vuelva a ejecutar el compilador. Para obtener información sobre errores específicos, use el cuadro de búsqueda de la parte superior de esta página para buscar el número de error.

1. Para ejecutar el programa, escriba `simple` en el símbolo del sistema.

   El programa muestra este texto y, a continuación, se cierra:

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   Enhorabuena, ha compilado y ejecutado un programa de C con la línea de comandos.

## <a name="next-steps"></a>Pasos siguientes

Este ejemplo "Hola mundo" es el programa de C más sencillo que se puede crear. Los programas reales contienen archivos de encabezado y más archivos de código fuente, vinculan a bibliotecas y llevan a cabo un trabajo útil.

Puede seguir los pasos de este tutorial para crear su propio código de C, en lugar de escribir el del ejemplo que se muestra. También puede crear muchos programas de ejemplo de código de C que encontrará en otras partes. Para compilar un programa que tiene archivos de código fuente adicionales, escríbalos todos en la línea de comandos, de esta forma:

`cl file1.c file2.c file3.c`

El compilador genera un programa llamado file1.exe. Para cambiar el nombre a program1.exe, agregue una opción del enlazador [/out](reference/out-output-file-name.md):

`cl file1.c file2.c file3.c /link /out:program1.exe`

Para detectar más errores de programación de forma automática, se recomienda compilar mediante la opción de nivel de advertencia [/W3](reference/compiler-option-warning-level.md) o [/W4](reference/compiler-option-warning-level.md):

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

El compilador (cl.exe) tiene muchas más opciones que se pueden aplicar para compilar, optimizar, depurar y analizar el código. Para obtener una lista rápida, escriba `cl /?` en el símbolo del sistema para desarrolladores. También puede compilar y vincular por separado, así como aplicar las opciones del enlazador en escenarios de compilación más complejos. Para obtener más información sobre el uso y las opciones del compilador y del enlazador, vea [Referencia de compilación de C/C++](reference/c-cpp-building-reference.md).

Puede usar NMAKE y archivos Make, o MSBuild y archivos del proyecto, para configurar y compilar proyectos más complejos en la línea de comandos. Para obtener más información sobre el uso de estas herramientas, consulte [Referencia de NMAKE](reference/nmake-reference.md) y [MSBuild](msbuild-visual-cpp.md).

Los lenguajes C y C++ son similares, pero no idénticos. El compilador de Microsoft C/C++ (MSVC) usa una regla simple para determinar qué lenguaje se usa al compilar el código. De forma predeterminada, el compilador de MSVC trata todos los archivos que finalizan en .c como código fuente de C, y todos los archivos que finalizan en .cpp como código fuente de C++. Para hacer que el compilador trate todos los archivos como de C con independencia de la extensión del nombre de archivo, use la opción [/Tc](reference/tc-tp-tc-tp-specify-source-file-type.md) del compilador.

MSVC admite el estándar ISO C99, pero no es totalmente compatible. En la mayoría de los casos, el código de C portable se compilará y se ejecutará según lo previsto. Visual C++ no es compatible con la mayoría de los cambios en ISO C11. Ciertas funciones de biblioteca y nombres de función POSIX están en desuso en MSVC. Las funciones se admiten, pero los nombres preferidos han cambiado. Para obtener más información, vea [Características de seguridad de CRT](../c-runtime-library/security-features-in-the-crt.md) y [Advertencia del compilador (nivel 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Vea también

[Tutorial: Crear un programa de C++ estándar (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[Referencia del lenguaje C](../c-language/c-language-reference.md)<br/>
[Proyectos y sistemas de compilación](projects-and-build-systems-cpp.md)<br/>
[Compatibilidad](../c-runtime-library/compatibility.md)
