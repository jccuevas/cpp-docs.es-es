---
title: 'Tutorial: Compilar un programa escrito en C en la línea de comandos'
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335262"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>Tutorial: Compilar un programa escrito en C en la línea de comandos

Visual C++ incluye un compilador de C que puede usar para crear todo, desde programas de consola básicos hasta aplicaciones completas de escritorio de Windows, aplicaciones móviles y mucho más.

En este tutorial se muestra cómo crear un programa C básico de estilo "Hola, mundo" mediante un editor de texto y, a continuación, compilarlo en la línea de comandos. Si prefiere trabajar en C++ en la línea de comandos, consulte Tutorial: Compilación de [un programa C++ nativo en la línea](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)de comandos . Si desea probar el IDE de Visual Studio en lugar de usar la línea de comandos, vea [Tutorial: Trabajar con proyectos y soluciones (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) o Usar el IDE de Visual Studio para el desarrollo de [escritorios de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="prerequisites"></a>Prerrequisitos

Para completar este tutorial, debe haber instalado Visual Studio y los componentes opcionales de Visual C++, o las herramientas de compilación para Visual Studio.

Visual Studio es un potente entorno de desarrollo integrado que admite un editor completo, administradores de recursos, depuradores y compiladores para muchos lenguajes y plataformas. Para obtener información sobre estas características y cómo descargar e instalar Visual Studio, incluida la edición gratuita de Visual Studio Community, vea [Instalar Visual Studio](/visualstudio/install/install-visual-studio).

La versión de Herramientas de compilación para Visual Studio de Visual Studio instala solo el conjunto de herramientas de línea de comandos, los compiladores, las herramientas y las bibliotecas que necesita para compilar programas C y C++. Es perfecto para construir laboratorios o ejercicios en el aula e instala relativamente rápido. Para instalar solo el conjunto de herramientas de línea de comandos, descargue Herramientas de compilación para Visual Studio desde la página de descargas de [Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) y ejecute el instalador. En el instalador de Visual Studio, seleccione la carga de trabajo herramientas de **compilación de C++** y elija **Instalar**.

Para poder crear un programa C o C++ en la línea de comandos, debe comprobar que las herramientas están instaladas y que puede acceder a ellas desde la línea de comandos. Visual C++ tiene requisitos complejos para que el entorno de línea de comandos encuentre las herramientas, los encabezados y las bibliotecas que utiliza. **No puede usar Visual C++ en una ventana** de símbolo del sistema sin necesidad de preparación. Necesita una ventana de *símbolo del sistema para desarrolladores,* que es una ventana de símbolo del sistema normal que tiene todas las variables de entorno necesarias establecidas. Afortunadamente, Visual C++ instala accesos directos para iniciar los símbolodel del sistema para desarrolladores que tienen el entorno configurado para las compilaciones de línea de comandos. Desafortunadamente, los nombres de los accesos directos del símbolo del sistema para desarrolladores y dónde se encuentran son diferentes en casi todas las versiones de Visual C++ y en diferentes versiones de Windows. La primera tarea del tutorial consiste en encontrar el acceso directo adecuado para usar.

> [!NOTE]
> Un acceso directo del símbolo del sistema para desarrolladores establece automáticamente las rutas de acceso correctas para el compilador y las herramientas, así como para los encabezados y bibliotecas necesarios. Algunos de estos valores son diferentes para cada configuración de compilación. Debe establecer estos valores de entorno usted mismo si no utiliza uno de los accesos directos. Para más información, vea [Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](setting-the-path-and-environment-variables-for-command-line-builds.md). Dado que el entorno de compilación es complejo, se recomienda encarecidamente usar un acceso directo del símbolo del sistema para desarrolladores en lugar de crear el suyo propio.

Estas instrucciones varían en función de la versión de Visual Studio que esté utilizando. Para ver la documentación de su versión preferida de Visual Studio, use el control Selector de **versiones.** Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker range="vs-2019"

## <a name="open-a-developer-command-prompt-in-visual-studio-2019"></a>Abra un símbolo del sistema para desarrolladores en Visual Studio 2019

Si ha instalado Visual Studio 2019 en Windows 10, abra el menú Inicio y, a continuación, desplácese hacia abajo y abra la carpeta **Visual Studio 2019** (no la aplicación Visual Studio 2019). Elija **el símbolo del sistema del desarrollador para VS 2019** para abrir la ventana del símbolo del sistema.

Si usa una versión diferente de Windows, busque en el menú Inicio o en la página Inicio una carpeta de herramientas de Visual Studio que contenga un acceso directo del símbolo del sistema para desarrolladores. También puede usar la función de búsqueda de Windows para buscar "símbolo del sistema para desarrolladores" y elegir uno que coincida con la versión instalada de Visual Studio. Utilice el acceso directo para abrir la ventana del símbolo del sistema.

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-developer-command-prompt-in-visual-studio-2017"></a>Abra un símbolo del sistema para desarrolladores en Visual Studio 2017

Si ha instalado Visual Studio 2017 en Windows 10, abra el menú Inicio y, a continuación, desplácese hacia abajo y abra la carpeta **Visual Studio 2017** (no la aplicación Visual Studio 2017). Elija **el símbolo del sistema del desarrollador para VS 2017** para abrir la ventana del símbolo del sistema.

Si está ejecutando una versión diferente de Windows, busque en el menú Inicio o en la página Inicio una carpeta de herramientas de Visual Studio que contenga un acceso directo del símbolo del sistema para desarrolladores. También puede usar la función de búsqueda de Windows para buscar "símbolo del sistema para desarrolladores" y elegir uno que coincida con la versión instalada de Visual Studio. Utilice el acceso directo para abrir la ventana del símbolo del sistema.

::: moniker-end

::: moniker range="vs-2015"

## <a name="open-a-developer-command-prompt-in-visual-studio-2015"></a>Abra un símbolo del sistema para desarrolladores en Visual Studio 2015

Si ha instalado Microsoft Visual C++ Build Tools 2015 en Windows 10, abra el menú **Inicio** y, a continuación, desplácese hacia abajo y abra la carpeta Herramientas de compilación de **Visual C++.** Elija **Visual C++ 2015 x86 Native Tools Símbolo del sistema** para abrir la ventana del símbolo del sistema.

Si está ejecutando una versión diferente de Windows, busque en el menú Inicio o en la página Inicio una carpeta de herramientas de Visual Studio que contenga un acceso directo del símbolo del sistema para desarrolladores. También puede usar la función de búsqueda de Windows para buscar "símbolo del sistema para desarrolladores" y elegir uno que coincida con la versión instalada de Visual Studio. Utilice el acceso directo para abrir la ventana del símbolo del sistema.

::: moniker-end

A continuación, compruebe que el símbolo del sistema para desarrolladores de Visual C++ está configurado correctamente. En la ventana del `cl` símbolo del sistema, ingrese y verifique que la salida se vea algo como esto:

```Output
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

usage: cl [ option... ] filename... [ /link linkoption... ]
```

Puede haber diferencias en el directorio actual o los números de versión, dependiendo de la versión de Visual C++ y las actualizaciones instaladas. Si la salida anterior es similar a la que ve, está listo para compilar programas C o C++ en la línea de comandos.

> [!NOTE]
> Si recibe un error como "'cl' no se reconoce como un comando interno o externo, programa operable o archivo por lotes", error C1034 o error LNK1104 al ejecutar el comando **cl,** entonces no está utilizando un símbolo del sistema para desarrolladores o algo está mal con la instalación de Visual C++. Debe solucionar este problema antes de poder continuar.

Si no puede encontrar el acceso directo del símbolo del sistema `cl`para desarrolladores, o si recibe un mensaje de error al escribir , la instalación de Visual C++ puede tener un problema. Si usa Visual Studio 2017 o posterior, intente reinstalar el desarrollo de escritorio con carga de trabajo **C++** en el instalador de Visual Studio. Para obtener más información, vea [Instalar compatibilidad con C++ en Visual Studio](vscpp-step-0-installation.md). O bien, vuelva a instalar las herramientas de compilación desde la página de descargas de [Visual Studio.](https://visualstudio.microsoft.com/downloads/) No pases a la siguiente sección hasta que esto funcione. Para obtener más información acerca de la instalación y solución de problemas de Visual Studio, vea [Instalar Visual Studio](/visualstudio/install/install-visual-studio).

> [!NOTE]
> Según la versión de Windows en el equipo y la configuración de seguridad del sistema, es posible que tenga que hacer clic con el botón derecho para abrir el menú contextual del acceso directo del símbolo del sistema para desarrolladores y, a continuación, elija **Ejecutar como administrador** para compilar y ejecutar correctamente el programa que cree siguiendo este tutorial.

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>Cree un archivo de origen de C y compílelo en la línea de comandos

1. En la ventana del `cd c:\` símbolo del sistema para desarrolladores, escriba para cambiar el directorio de trabajo actual a la raíz de la unidad C:. A continuación, escriba `md c:\simple` para crear `cd c:\simple` un directorio y, a continuación, escriba para cambiar a ese directorio. Este directorio contendrá el archivo de origen y el programa compilado.

1. Escriba `notepad simple.c` en el símbolo del sistema para desarrolladores. En el cuadro de diálogo de alerta del Bloc de notas que aparece, elija **Sí** para crear un nuevo archivo simple.c en el directorio de trabajo.

1. En el Bloc de notas, introduzca las siguientes líneas de código:

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. En la barra de menús del Bloc de notas, elija **Guardar** > **archivo** para guardar simple.c en el directorio de trabajo.

1. Vuelva a la ventana del símbolo del sistema para desarrolladores. Ingrese `dir` en el símbolo del sistema para enumerar el contenido del directorio c:-simple. Debería ver el archivo de origen simple.c en la lista de directorios, que tiene un aspecto similar a:

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

   Las fechas y otros detalles diferirán en su computadora. Si no ve el archivo de código fuente, simple.c, asegúrese de que ha cambiado al directorio c:-simple que ha creado y, en el Bloc de notas, asegúrese de que ha guardado el archivo de origen en este directorio. Asegúrese también de que ha guardado el código fuente con una extensión de nombre de archivo .c, no con una extensión .txt.

1. Para compilar el `cl simple.c` programa, escriba en el símbolo del sistema para desarrolladores.

   Puede ver el nombre del programa ejecutable, simple.exe, en las líneas de información de salida que muestra el compilador:

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
   > Si recibe un error como "'cl' no se reconoce como un comando interno o externo, programa operable o archivo por lotes", error C1034 o error LNK1104, el símbolo del sistema para desarrolladores no está configurado correctamente. Para obtener información sobre cómo solucionar este problema, vuelva a la sección **Abrir un símbolo del sistema** para desarrolladores.

   > [!NOTE]
   > Si obtiene un error o advertencia de compilador o vinculador diferente, revise el código fuente para corregir los errores y, a continuación, guárdelo y vuelva a ejecutar el compilador. Para obtener información acerca de errores específicos, utilice el cuadro de búsqueda en la parte superior de esta página para buscar el número de error.

1. Para ejecutar el `simple` programa, escriba en el símbolo del sistema.

   El programa muestra este texto y, a continuación, se cierra:

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   Enhorabuena, ha compilado y ejecutado un programa C mediante la línea de comandos.

## <a name="next-steps"></a>Pasos siguientes

Este ejemplo de "Hola, mundo" es tan simple como un programa C puede obtener. Los programas del mundo real tienen archivos de encabezado y más archivos de origen, enlace en bibliotecas y hacen un trabajo útil.

Puede usar los pasos de este tutorial para crear su propio código C en lugar de escribir el código de ejemplo que se muestra. También puede crear muchos programas de ejemplo de código C que encuentre en otro lugar. Para compilar un programa que tenga archivos de código fuente adicionales, introdúzcalos todos en la línea de comandos, como:

`cl file1.c file2.c file3.c`

El compilador genera un programa denominado file1.exe. Para cambiar el nombre a program1.exe, agregue una opción de vinculador [/out:](reference/out-output-file-name.md)

`cl file1.c file2.c file3.c /link /out:program1.exe`

Y para detectar más errores de programación automáticamente, le recomendamos compilar mediante la opción de nivel de advertencia [/W3](reference/compiler-option-warning-level.md) o [/W4:](reference/compiler-option-warning-level.md)

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

El compilador, cl.exe, tiene muchas más opciones que puede aplicar para compilar, optimizar, depurar y analizar el código. Para obtener una `cl /?` lista rápida, escriba en el símbolo del sistema para desarrolladores. También puede compilar y vincular por separado y aplicar opciones de vinculador en escenarios de compilación más complejos. Para obtener más información sobre las opciones y el uso del compilador y del vinculador, consulte Referencia de creación de [C/C++.](reference/c-cpp-building-reference.md)

Puede usar NMAKE y makefiles, o MSBuild y archivos de proyecto para configurar y compilar proyectos más complejos en la línea de comandos. Para obtener más información sobre el uso de estas herramientas, vea [NMAKE Reference](reference/nmake-reference.md) y [MSBuild](msbuild-visual-cpp.md).

Los idiomas C y C+ son similares, pero no los mismos. El compilador de Microsoft C/C++ (MSVC) usa una regla simple para determinar qué lenguaje usar cuando compila el código. De forma predeterminada, el compilador MSVC trata todos los archivos que terminan en .c como código fuente de C y todos los archivos que terminan en .cpp como código fuente C++. Para forzar al compilador a tratar todos los archivos como C no dependientes de la extensión de nombre de archivo, use la opción del compilador [/Tc.](reference/tc-tp-tc-tp-specify-source-file-type.md)

MSVC es compatible con la norma ISO C99, pero no es estrictamente compatible. En la mayoría de los casos, el código C portátil se compilará y ejecutará según lo previsto. Visual C++ no admite la mayoría de los cambios en ISO C11. MSVC desuso ciertas funciones de biblioteca y nombres de funciones POSIX. Se admiten las funciones, pero los nombres preferidos han cambiado. Para obtener más información, consulte Características de [seguridad en CRT](../c-runtime-library/security-features-in-the-crt.md) y Advertencia del compilador [(nivel 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Consulte también

[Tutorial: Crear un programa de C++ estándar (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[C Referencia del lenguaje](../c-language/c-language-reference.md)<br/>
[Proyectos y sistemas de compilación](projects-and-build-systems-cpp.md)<br/>
[Compatibilidad](../c-runtime-library/compatibility.md)
