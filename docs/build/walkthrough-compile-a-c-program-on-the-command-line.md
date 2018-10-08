---
title: 'Tutorial: Compilar un programa de C en la línea de comandos | Microsoft Docs'
ms.custom: conceptual
ms.date: 09/24/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8b48093641982f171a5d8b43fa70d7694122263
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861270"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>Tutorial: Compilar un programa de C en la línea de comandos

Visual C++ incluye un compilador de C que puede usar para crear desde programas de consola básicas hasta aplicaciones completas de escritorio de Windows, aplicaciones móviles y mucho más.

En este tutorial se muestra cómo crear un básico "Hola, mundo": el programa de C de estilo mediante el uso de un texto editor y, a continuación, compilarlo en la línea de comandos. Si prefiere trabajar en C++ en la línea de comandos, consulte [Tutorial: compilar un programa de C++ nativo en la línea de comandos](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md). Si desea probar el IDE de Visual Studio en lugar de usar la línea de comandos, consulte [Tutorial: trabajar con proyectos y soluciones (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) o [mediante el IDE de Visual Studio para el desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="prerequisites"></a>Requisitos previos

Para completar este tutorial, deben haber instalado Visual Studio y los componentes opcionales de Visual C++ o las herramientas de compilación para Visual Studio.

Visual Studio es un entorno de desarrollo integrado que admite un editor completo, los administradores de recursos, depuradores y los compiladores para numerosos lenguajes y plataformas. Para obtener información sobre estas características y cómo descargar e instalar Visual Studio, incluida la edición de Visual Studio Community gratis, consulte [instalar Visual Studio](/visualstudio/install/install-visual-studio).

Build Tools para Visual Studio, versión de Visual Studio instala solo el conjunto de herramientas de línea de comandos, compiladores, herramientas y las bibliotecas que necesita para compilar programas de C y C++. Es perfecto para laboratorios de compilación o aula ejercita e instala de forma relativamente rápida. Para instalar solo el conjunto de herramientas de línea de comandos, descargue [Build Tools para Visual Studio](https://go.microsoft.com/fwlink/p/?linkid=875721) y ejecute el instalador.

Antes de generar un programa de C o C++ en la línea de comandos, debe comprobar que las herramientas están instaladas y que puede acceder a ellos desde la línea de comandos. Visual C++ tiene requisitos complejos para el entorno de línea de comandos encontrar las herramientas, encabezados y bibliotecas que utiliza. **No se puede utilizar Visual C++ en una ventana del símbolo del sistema sin formato** sin una preparación. Necesita un *símbolo* ventana, que es una ventana de símbolo del sistema normal que tenga todas las variables de entorno necesarias. Afortunadamente, Visual C++ instala accesos directos para iniciar los símbolos del sistema para desarrolladores que tienen el entorno configurado para las compilaciones de línea de comandos. Lamentablemente, los nombres de los accesos directos del símbolo del sistema para desarrolladores y dónde están ubicados son diferentes en casi todas las versiones de Visual C++ y en diferentes versiones de Windows. La primera tarea del tutorial consiste en encontrar el método abreviado de derecho a usar.

> [!NOTE]
> Un acceso directo del símbolo para desarrolladores establece automáticamente las rutas de acceso correctas para el compilador y las herramientas y para los encabezados necesarios y las bibliotecas. Algunos de estos valores son diferentes para cada configuración de compilación. Deben establecer estos valores de entorno usted mismo si no usa uno de los métodos abreviados. Para obtener más información, consulte [establecer la ruta de acceso y las Variables de entorno para compilaciones de línea de comandos](../build/setting-the-path-and-environment-variables-for-command-line-builds.md). Dado el entorno de compilación es complejo, se recomienda encarecidamente que usar un acceso directo del símbolo para desarrolladores en lugar de crear el suyo propio.

## <a name="open-a-developer-command-prompt"></a>Abra un símbolo del sistema para desarrolladores

1. Si ha instalado Visual Studio 2017 en Windows 10, abra el menú Inicio y, a continuación, desplácese hacia abajo y abra el **Visual Studio 2017** carpeta (no en la aplicación de Visual Studio 2017). Elija **símbolo del sistema para desarrolladores para VS 2017** para abrir la ventana de símbolo del sistema.

   Si ha instalado Microsoft Visual C++ Build Tools 2015 en Windows 10, abra el **iniciar** menú y, a continuación, desplácese hacia abajo y abra el **Visual C++ Build Tools** carpeta. Elija **línea de comandos de herramientas nativo de Visual C++ 2015 x86** para abrir la ventana de símbolo del sistema.

   Si está usando una versión diferente de Visual Studio o ejecutan una versión diferente de Windows, busque en el menú Inicio o página de inicio de una carpeta de herramientas de Visual Studio que contenga un acceso directo del símbolo para desarrolladores. También puede usar la función de búsqueda de Windows para buscar "símbolo" y elija una que coincida con la versión instalada de Visual Studio. Use el método abreviado para abrir la ventana de símbolo del sistema.

1. A continuación, compruebe que la línea de comandos para desarrolladores de Visual C++ se ha configurado correctamente. En la ventana de símbolo del sistema, escriba `cl` y compruebe que el resultado es similar a esto:

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   Puede haber diferencias en el directorio actual o números de versión, según la versión de Visual C++ y las actualizaciones instaladas. Si la salida anterior es similar a lo que ve, estará listo para compilar programas de C o C++ en la línea de comandos.

   > [!NOTE]
   > Si se produce un error, como "'cl' no se reconoce como un comando interno o externo, programa operable o archivo por lotes," error de C1034 o LNK1104 al ejecutar el **cl** de comandos, o bien no está usando un símbolo del sistema, o algo va mal con la instalación de Visual C++. Debe corregir este problema antes de continuar.

   Si no se encuentra el programador acceso directo del símbolo del sistema, o si recibe un mensaje de error al escribir `cl`, a continuación, la instalación de Visual C++ puede tener un problema. Si usa Visual Studio 2017, intente volver a instalar el **desarrollo de escritorio con C++** carga de trabajo en el instalador de Visual Studio. Para obtener más información, consulte [compatibilidad Install C++ en Visual Studio](../build/vscpp-step-0-installation.md). O bien, vuelva a instalar el [Build Tools para Visual Studio](https://go.microsoft.com/fwlink/p/?linkid=875721). No vaya a la sección siguiente hasta que esto funcione. Para obtener más información sobre la instalación y solución de problemas de Visual Studio, consulte [instalar Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > Según la versión de Windows en el equipo y la configuración de seguridad del sistema, es posible que deba haga doble clic para abrir el menú contextual para el acceso de directo del símbolo del sistema para desarrolladores y, a continuación, elija **ejecutar como administrador** a compilar y ejecutar el programa que se crea siguiendo este tutorial correctamente.

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>Crear un archivo de código fuente de C y compilarlo en la línea de comandos

1. En la ventana de símbolo del sistema para desarrolladores, escriba `cd c:\` para cambiar el directorio de trabajo actual a la raíz de la unidad C:. A continuación, escriba `md c:\simple` para crear un directorio y, a continuación, escriba `cd c:\simple` para cambiar a ese directorio. Este directorio contendrá el archivo de origen y el programa compilado.

1. Escriba `notepad simple.c` en el símbolo del sistema de desarrollador. En el Bloc de notas alerta cuadro de diálogo que aparece, elija **Sí** para crear un nuevo archivo simple.c en el directorio de trabajo.

1. En el Bloc de notas, escriba las siguientes líneas de código:

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. En la barra de menús del Bloc de notas, elija **archivo** > **guardar** guardar simple.c en el directorio de trabajo.

1. Cambie a la ventana de símbolo del sistema para desarrolladores. Escriba `dir` en el símbolo del sistema para mostrar el contenido del directorio de c:\simple. Debería ver el simple.c del archivo de origen en la lista de directorios, que se parece algo como:

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

   Las fechas y otros detalles variarán en su equipo. Si no ve el archivo de código fuente, asegúrese de que ha cambiado en el directorio de c:\simple que creó simple.c y en el Bloc de notas, asegúrese de que guardó el archivo de código fuente en este directorio. Además, asegúrese de que ha guardado el código fuente con una extensión de nombre de archivo .c, no una extensión. txt.

1. Para compilar el programa, escriba `cl simple.c` en el símbolo del sistema de desarrollador.

   Puede ver el nombre del programa ejecutable, simple.exe en las líneas de información de salida que muestra el compilador:

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
   > Si se produce un error, como "'cl' no se reconoce como un comando interno o externo, programa operable o archivo por lotes," error de C1034 o LNK1104, el símbolo del sistema para desarrolladores no está configurado correctamente. Para obtener información sobre cómo solucionar este problema, vuelva a la **abra un símbolo del sistema para desarrolladores** sección.

   > [!NOTE]
   > Si se produce una advertencia o error del vinculador o compilador diferentes, revise el código fuente para corregir los errores, a continuación, guárdelo y vuelva a ejecutar el compilador. Para obtener información sobre los errores específicos, use el cuadro de búsqueda en la parte superior de esta página para buscar el número de error.

1. Para ejecutar el programa, escriba `simple` en el símbolo del sistema.

   El programa muestra este texto y, a continuación, se cierra:

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   Enhorabuena, acaba de compilar y ejecutar un programa de C mediante el uso de la línea de comandos.

## <a name="next-steps"></a>Pasos siguientes

Es tan sencillo como un programa de C puede obtener este ejemplo "Hello, World". Programas del mundo real tienen archivos de encabezado y más archivos de código fuente, vincular en bibliotecas, y realizar trabajo útil.

Puede usar los pasos de este tutorial para crear su propio código de C en lugar de escribir el código de ejemplo que se muestra. También puede crear muchos programas de ejemplo de código de C que encuentre en otro lugar. Para compilar un programa que tiene archivos de código fuente adicionales, escríbalos en la línea de comandos, como:

`cl file1.c file2.c file3.c`

El compilador genera un programa llamado file1.exe. Para cambiar el nombre a program1.exe, agregue un [/out](../build/reference/out-output-file-name.md) opción del vinculador:

`cl file1.c file2.c file3.c /link /out:program1.exe`

Y para detectar errores de programación más automáticamente, se recomienda compilar mediante el uso del [/w3](../build/reference/compiler-option-warning-level.md) o [/W4](../build/reference/compiler-option-warning-level.md) opción de nivel de advertencia:

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

El compilador, cl.exe, tiene muchas más opciones que puede aplicar para crear, optimizar, depurar y analizar el código. Para obtener una lista rápida, escriba `cl /?` en el símbolo del sistema de desarrollador. También puede compilar y vincular por separado y aplicar las opciones del vinculador en escenarios más complejos de compilación. Para obtener más información sobre el compilador y las opciones del vinculador y uso, consulte [C/C ++ Building Reference](../build/reference/c-cpp-building-reference.md).

Puede usar NMAKE y archivos MAKE o archivos de proyecto y MSBuild para configurar y compilar los proyectos más complejos en la línea de comandos. Para obtener más información sobre el uso de estas herramientas, consulte [referencia de NMAKE](../build/nmake-reference.md) y [MSBuild](../build/msbuild-visual-cpp.md).

Los lenguajes C y C++ son similares, pero no es el mismo. El compilador de Visual C++ usa una regla sencilla para determinar el idioma que desea utilizar cuando se compila el código. De forma predeterminada, el compilador de Visual C++ trata todos los archivos que finalizan en .c como código fuente de C, y todos los archivos que finalizan en .cpp como código fuente de C++. Para forzar al compilador que trate todos los archivos como C no dependientes de la extensión de nombre de archivo, use el [/TC](../build/reference/tc-tp-tc-tp-specify-source-file-type.md) opción del compilador.

El compilador de C de Visual C++ es compatible con el estándar ISO C99, pero no es totalmente compatible. En la mayoría de los casos, el código de C portátil compilará y ejecutará según lo previsto. Visual C++ no admite la mayoría de los cambios en ISO C11. Ciertas funciones de biblioteca y los nombres de función POSIX están en desuso por el compilador de Visual C++. Se admiten las funciones, pero han cambiado los nombres preferidos. Para obtener más información, consulte [características de seguridad de CRT](../c-runtime-library/security-features-in-the-crt.md) y [advertencia del compilador (nivel 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Vea también

[Tutorial: Crear un programa de C++ estándar (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[Referencia del lenguaje C](../c-language/c-language-reference.md)<br/>
[Compilación de programas de C/C++](../build/building-c-cpp-programs.md)<br/>
[Compatibilidad](../c-runtime-library/compatibility.md)
