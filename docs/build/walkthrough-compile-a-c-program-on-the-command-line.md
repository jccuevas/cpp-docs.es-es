---
title: "Tutorial: Compilar un programa de C en la línea de comandos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
caps.latest.revision: "46"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7520e2d78c924ee21c489d2e8327c4bda9b973aa
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>Tutorial: Compilar un programa de C en la línea de comandos
Visual C++ incluye un compilador de C que puede usar para crear cualquier cosa, desde los programas de consola básicas hasta completas aplicaciones de escritorio de Windows, aplicaciones móviles y mucho más.  
  
 Este tutorial muestra cómo crear un básico, "Hello, World"-programa de C de estilo mediante un texto editor y, a continuación, compilarlo en la línea de comandos. Si prefiere trabajar en C++ en la línea de comandos, consulte [Tutorial: compilar un programa de C++ nativo en la línea de comandos](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md). Si le gustaría intentarlo el IDE de Visual Studio en lugar de usar la línea de comandos, consulte [Tutorial: trabajar con proyectos y soluciones (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) o [mediante el IDE de Visual Studio para el desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para completar este tutorial, debe haber instalado Visual Studio y los componentes opcionales de Visual C++ o Microsoft Visual C++ generar herramientas.  
  
 Visual Studio es un entorno de desarrollo integrado que admite un editor con todas las características, los administradores de recursos, depuradores y compiladores para muchos lenguajes y plataformas. Para obtener información sobre estas características y cómo descargar e instalar Visual Studio, incluida la edición de Visual Studio Community gratis, consulte [VisualStudio.com](https://www.visualstudio.com/).  
  
 Las herramientas de compilación de Visual Studio instala los compiladores de línea de comandos, herramientas y las bibliotecas que necesita para compilar programas de C y C++. Es perfecto para los laboratorios de compilación o aula ejercita e instala relativamente rápidamente. Para instalar solamente las herramientas de línea de comandos, descargue [herramientas de compilación de Visual Studio](https://go.microsoft.com/fwlink/p/?linkid=840931) y ejecute el programa de instalación. Para obtener más información, consulte [herramientas de compilación de Visual C++](http://landinghub.visualstudio.com/visual-cpp-build-tools).  
  
 Antes de generar un programa de C o C++ en la línea de comandos, debe comprobar que se instalan las herramientas, y que puede tener acceso a ellos desde la línea de comandos. Visual C++ tiene requisitos complejos para el entorno de línea de comandos para encontrar herramientas, encabezados y bibliotecas que utiliza. **No se puede usar Visual C++ en una ventana del símbolo del sistema sin formato**. Necesita un *símbolo* ventana, que es una ventana de símbolo del sistema normal que tiene todas las variables de entorno necesarias establecido. Afortunadamente, Visual C++ instala accesos directos para iniciar el símbolo del sistema de desarrollador que tienen el entorno configurada para compilaciones de línea de comandos. Desgraciadamente, los nombres de los accesos directos del símbolo del sistema para desarrolladores y dónde se encuentran son diferentes en casi todas las versiones de Visual C++ y en diferentes versiones de Windows. La primera tarea del tutorial consiste en buscar el método abreviado de derecho a usar.  
  
> [!NOTE]
>  Un acceso directo del símbolo para desarrolladores establece automáticamente las rutas de acceso correcta para el compilador y las herramientas y para los encabezados necesarios y bibliotecas. Algunos de estos valores son diferentes para cada configuración de compilación. Debe establecer estos valores de entorno de usted mismo si no usa uno de los métodos abreviados. Para obtener más información, consulte [establecer la ruta de acceso y las Variables de entorno para compilaciones de línea de comandos](../build/setting-the-path-and-environment-variables-for-command-line-builds.md). Dado que el entorno de compilación es complejo, se recomienda encarecidamente que utilizar un acceso directo del símbolo para desarrolladores en lugar de generar su propia.  
  
## <a name="open-a-developer-command-prompt"></a>Abra un símbolo del sistema para desarrolladores  
  
1.  Si ha instalado Visual Studio de 2017 en Windows 10, abra el menú Inicio y, a continuación, desplácese hacia abajo y abra el **2017 de Visual Studio** carpeta (no en la aplicación de Visual Studio de 2017). Elija **símbolo del sistema para desarrolladores de VS 2017** para abrir la ventana de símbolo del sistema.  
  
     Si ha instalado Microsoft Visual C++ crear herramientas de 2015 en Windows 10, abra el **iniciar** menú y, a continuación, desplácese hacia abajo y abra el **herramientas de compilación de Visual C++** carpeta. Elija **línea de comandos de herramientas nativo de Visual C++ 2015 x86** para abrir la ventana de símbolo del sistema.  
  
     Si está usando una versión diferente de Visual Studio o se ejecuta una versión distinta de Windows, busque en el menú de inicio o página de inicio de una carpeta de herramientas de Visual Studio que contenga un acceso directo del símbolo para desarrolladores. También puede utilizar la función de búsqueda de Windows para buscar "símbolo" y elija una que coincida con la versión instalada de Visual Studio. Use el método abreviado para abrir la ventana de símbolo del sistema.  
  
2.  A continuación, compruebe que la línea de comandos de desarrollador de Visual C++ se ha configurado correctamente. En la ventana de símbolo del sistema, escriba `cl` y comprobar que el resultado tiene un aspecto similar al siguiente:  
  
    ```Output  
    C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl  
    Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86  
    Copyright (C) Microsoft Corporation.  All rights reserved.  
    
    usage: cl [ option... ] filename... [ /link linkoption... ]  
    
    C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>  
    ```  
  
     Puede haber diferencias en el directorio actual o números de versión, según la versión de Visual C++ y las actualizaciones instaladas. Si esto es similar a como se muestra, a continuación, está listo para compilar programas de C o C++ en la línea de comandos.  
  
    > [!NOTE]
    >  Si se produce un error, como "'cl' no se reconoce como un comando interno o externo, programa operable o archivo por lotes,", o los errores C1034 o LNK1104 al ejecutar el **cl** comando, a continuación, ya sea que no usa un símbolo del sistema, o algo no funciona correctamente con la instalación de Visual C++. Debe corregir este problema antes de continuar.  
  
     Si no se puede encontrar el programador acceso directo del símbolo del sistema, o si recibe un mensaje de error al escribir `cl`, a continuación, la instalación de Visual C++ puede tener un problema. Intente volver a instalar el componente de Visual C++ en Visual Studio, o volver a instalar las herramientas de compilación de Visual Studio. No vaya a la sección siguiente hasta que esto funcione. Para obtener más información sobre la instalación y solución de problemas de Visual C++, vea [instalar Visual Studio](/visualstudio/install/install-visual-studio).  
  
    > [!NOTE]
    >  Según la versión de Windows en el equipo y la configuración de seguridad del sistema, es posible que deba haga clic en para abrir el menú contextual para el acceso directo del símbolo desarrollador y, a continuación, elija **ejecutar como administrador** para compilar y ejecutar el programa que se crea siguiendo este tutorial correctamente.  
  
## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>Crear un archivo de código fuente de C y compilarlo en la línea de comandos  
  
1.  En la ventana de símbolo del sistema para desarrolladores, escriba **cd c:\\**  para cambiar el directorio de trabajo actual a la raíz de la unidad C:. A continuación, escriba **md c:\simple** para crear un directorio y, a continuación, escriba **c:\simple cd** para cambiar a ese directorio. Este es el directorio que contiene el archivo de origen y el programa compilado.  
  
2.  Escriba **simple.c el Bloc de notas** en el símbolo del sistema para desarrolladores. En el Bloc de notas alerta cuadro de diálogo que aparece, elija **Sí** para crear un nuevo archivo simple.c en el directorio de trabajo.  
  
3.  En el Bloc de notas, escriba las siguientes líneas de código:  
  
    ```C  
    #include <stdio.h>  
  
    int main()  
    {  
        printf("Hello, World! This is a native C program compiled on the command line.\n");  
        return 0;  
    }   
    ```  
  
4.  En la barra de menús del Bloc de notas, elija **archivo**, **guardar** guardar simple.c en el directorio de trabajo.  
  
5.  Vuelva a cambiar la ventana de símbolo del sistema para desarrolladores. Escriba **dir** en el símbolo del sistema para mostrar el contenido del directorio de c:\simple. Debería ver el simple.c del archivo de origen en la lista de directorios, que es algo parecido a esto:  
  
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
  
     Las fechas y otros detalles variarán en su equipo. Si no ve el archivo de código fuente, simple.c, asegúrese de que ha cambiado en el directorio de c:\simple creado y en el Bloc de notas, asegúrese de que había guarda el archivo de código fuente en este directorio. Además, asegúrese de que había guarda el código fuente con una extensión de nombre de archivo. c., no una extensión. txt.  
  
6.  Para compilar el programa, escriba **simple.c cl** en el símbolo del sistema para desarrolladores.  
  
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
    >  Si se produce un error, como "'cl' no se reconoce como un comando interno o externo, programa operable o archivo por lotes,", o los errores C1034 o LNK1104, el símbolo del sistema para desarrolladores no está configurado correctamente. Para obtener información sobre cómo solucionar este problema, vuelva a la **abrir un símbolo del sistema para desarrolladores** sección.  
  
    > [!NOTE]
    >  Si recibe una advertencia o error del vinculador o compilador diferentes, revise el código fuente para corregir los errores, a continuación, guárdelo y vuelva a ejecutar el compilador. Para obtener información sobre errores concretos, use el cuadro de búsqueda en esta página MSDN para buscar el número de error.  
  
7.  Para ejecutar el programa, escriba **simple** en el símbolo del sistema.  
  
     El programa muestra este texto y, a continuación, se cierra:  
  
    ```Output  
    Hello, World! This is a native C program compiled on the command line.  
    ```  
  
     Enhorabuena, simplemente ha compilado y ejecutar un programa de C mediante la línea de comandos.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Es tan sencillo como un programa de C puede obtener este ejemplo "Hola, mundo". Programas de mundo real tienen archivos de encabezado y varios archivos de código fuente, vincular en bibliotecas, y realizar un trabajo útil.  
  
 Puede usar los pasos en este tutorial para crear su propio código de C en lugar de escribir el código de ejemplo mostrado. También puede crear muchos programas de ejemplo de código de C que encuentre en otro lugar. Para compilar un programa que tiene varios archivos de código fuente, escríbalas todas en la línea de comandos, similar al siguiente:  
  
 `cl file1.c file2.c file3.c`  
  
 El compilador genera un programa llamado file1.exe. Para cambiar el nombre a program1.exe, agregue un [/out](../build/reference/out-output-file-name.md) opción del vinculador:  
  
 `cl file1.c file2.c file3.c /link /out:program1.exe`  
  
 Y para detectar errores de programación más automáticamente, se recomienda compilar utilizando la [/W3](../build/reference/compiler-option-warning-level.md) o [/W4](../build/reference/compiler-option-warning-level.md) opción de nivel de advertencia:  
  
 `cl /W4 file1.c file2.c file3.c /link /out:program1.exe`  
  
 El compilador, cl.exe, tiene muchas más opciones que puede aplicar para compilar, optimizar, depurar y analizar el código. ¿Para obtener una lista rápida, escriba **cl /?** en el símbolo del sistema para desarrolladores. También puede compilar y vincular por separado y aplicar las opciones del vinculador en escenarios de compilación más complejos. Para obtener más información sobre el compilador y las opciones del vinculador y uso, consulte [referencia de compilación de C/C ++](../build/reference/c-cpp-building-reference.md).  
  
 Puede usar NMAKE y MAKE (archivos) o archivos de proyecto y MSBuild para configurar y compilar proyectos más complejos en la línea de comandos. Para obtener más información sobre el uso de estas herramientas, consulte [referencia de NMAKE](../build/nmake-reference.md) y [MSBuild](../build/msbuild-visual-cpp.md).  
  
 Los lenguajes C y C++ son similares, pero no es el mismo. El compilador de Visual C++ usa una regla sencilla para determinar qué idioma que se usará cuando se compila el código. De forma predeterminada, el compilador de Visual C++ trata todos los archivos que finalizan en .c como código fuente de C, y todos los archivos que finalizan en .cpp como código fuente de C++. Para forzar al compilador que trate todos los archivos como C, independientemente de la extensión de nombre de archivo, use la [/TC](../build/reference/tc-tp-tc-tp-specify-source-file-type.md) opción del compilador.  
  
 El compilador de C de Visual C++ es generalmente compatible con el estándar ISO C99, pero no es totalmente compatible. En la mayoría de los casos, código portable de C se compile y ejecute según lo esperado. Visual C++ no admite la mayoría de los cambios en C11 ISO. Ciertas funciones de la biblioteca y los nombres de función POSIX están en desuso por el compilador de Visual C++. Se admiten las funciones, pero los nombres preferidos han cambiado. Para obtener más información, consulte [características de seguridad en CRT](../c-runtime-library/security-features-in-the-crt.md) y [C4996 de advertencia del compilador (nivel 3)](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Crear un programa estándar de C++ (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)   
 [Referencia del lenguaje C](../c-language/c-language-reference.md)   
 [Compilación de programas de C/C++](../build/building-c-cpp-programs.md)   
 [Compatibilidad](../c-runtime-library/compatibility.md)