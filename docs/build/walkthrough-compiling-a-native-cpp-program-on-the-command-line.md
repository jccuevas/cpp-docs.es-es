---
title: 'Tutorial: Compilar un programa de C++ nativo en la línea de comandos | Documentos de Microsoft'
ms.custom: conceptual
ms.date: 11/04/2016
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
ms.openlocfilehash: c2ba3d1da27b3300f6299e902c35157cfe421f5c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>Tutorial: Compilar un programa nativo de C++ en la línea de comandos
Visual C++ incluye un compilador de C++ de línea de comandos que puede usar para crear cualquier cosa, desde aplicaciones de consola básica para aplicaciones de la plataforma Universal de Windows, aplicaciones de escritorio, controladores de dispositivos y componentes. NET.  
  
 En este tutorial, creará un basic, "Hello, World"-programa de C++ de estilo mediante un texto editor y, a continuación, compilarlo en la línea de comandos. Si le gustaría intentarlo el IDE de Visual Studio en lugar de usar la línea de comandos, consulte [Tutorial: trabajar con proyectos y soluciones (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) o [mediante el IDE de Visual Studio para el desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
 En este tutorial, puede usar su propio programa de Visual C++ en lugar de escribir el que se muestra o usar un código de ejemplo de Visual C++ de otro artículo de ayuda.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para completar este tutorial, debe haber instalado Visual Studio y los componentes opcionales de Visual C++ o Microsoft Visual C++ generar herramientas.  
  
 Visual Studio es un entorno de desarrollo integrado que admite un editor con todas las características, los administradores de recursos, depuradores y compiladores para muchos lenguajes y plataformas. Para obtener información sobre estas características y cómo descargar e instalar Visual Studio, incluida la edición de Visual Studio Community gratis, consulte [VisualStudio.com](https://www.visualstudio.com/).  
  
 Las herramientas de compilación de Visual Studio instala los compiladores de línea de comandos, herramientas y las bibliotecas que necesita para compilar programas de C y C++. Es perfecto para los laboratorios de compilación o aula ejercita e instala relativamente rápidamente. Para instalar solamente las herramientas de línea de comandos, descargue [herramientas de compilación de Visual Studio](https://go.microsoft.com/fwlink/p/?linkid=840931) y ejecute el programa de instalación. Para obtener más información, consulte [herramientas de compilación de Visual C++](http://landinghub.visualstudio.com/visual-cpp-build-tools).  
  
 Antes de generar un programa de C o C++ en la línea de comandos, debe comprobar que se instalan las herramientas, y que puede tener acceso a ellos desde la línea de comandos. Visual C++ tiene requisitos complejos para el entorno de línea de comandos para encontrar herramientas, encabezados y bibliotecas que utiliza. **No se puede usar Visual C++ en una ventana del símbolo del sistema sin formato**. Afortunadamente, Visual C++ instala accesos directos para iniciar un símbolo que tiene el entorno configurada para compilaciones de línea de comandos. Desgraciadamente, los nombres de los accesos directos del símbolo del sistema para desarrolladores y dónde se encuentran son diferentes en casi todas las versiones de Visual C++ y en diferentes versiones de Windows. La primera tarea del tutorial detecta uno derecho para que se utilice.  
  
> [!NOTE]
>  Un acceso directo del símbolo para desarrolladores establece automáticamente las rutas de acceso correcta para el compilador y las herramientas y para los encabezados necesarios y bibliotecas. Debe establecer estos valores de entorno de por sí mismo si se utiliza una ventana de símbolo del sistema normal. Para obtener más información, consulte [establecer la ruta de acceso y las Variables de entorno para compilaciones de línea de comandos](../build/setting-the-path-and-environment-variables-for-command-line-builds.md). Se recomienda que utilizar un acceso directo del símbolo para desarrolladores en lugar de generar su propia.  
  
### <a name="open-a-developer-command-prompt"></a>Abra un símbolo del sistema para desarrolladores  
  
1.  Si ha instalado Visual Studio de 2017 en Windows 10, abra el menú Inicio y elija **todas las aplicaciones**. Desplácese hacia abajo y abra el **2017 de Visual Studio** carpeta (no en la aplicación de Visual Studio de 2017). Elija **símbolo del sistema para desarrolladores de VS 2017** para abrir la ventana de símbolo del sistema.  
  
     Si ha instalado Microsoft Visual C++ crear herramientas de 2015 en Windows 10, abra el **iniciar** menú y elija **todas las aplicaciones**. Desplácese hacia abajo y abra el **herramientas de compilación de Visual C++** carpeta. Elija **línea de comandos de herramientas nativo de Visual C++ 2015 x86** para abrir la ventana de símbolo del sistema.  
  
     Si está usando una versión diferente de Visual Studio o se ejecuta una versión distinta de Windows, busque en el menú de inicio o página de inicio de una carpeta de herramientas de Visual Studio que contenga un acceso directo del símbolo para desarrolladores. También puede utilizar la función de búsqueda de Windows para buscar "símbolo" y elija una que coincida con la versión instalada de Visual Studio. Use el método abreviado para abrir la ventana de símbolo del sistema.  
  
2.  A continuación, compruebe que la línea de comandos de desarrollador de Visual C++ se ha configurado correctamente. En la ventana de símbolo del sistema, escriba `cl` y comprobar que el resultado tiene un aspecto similar al siguiente:  
  
    ```Output  
    C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl  
    Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86  
    Copyright (C) Microsoft Corporation.  All rights reserved.  
    
    usage: cl [ option... ] filename... [ /link linkoption... ]  
    ```  
  
     Puede haber diferencias en el directorio actual o números de versión, según la versión de Visual C++ y las actualizaciones instaladas. Si esto es similar a como se muestra, a continuación, está listo para compilar programas de C o C++ en la línea de comandos.  
  
    > [!NOTE]
    >  Si se produce un error, como "'cl' no se reconoce como un comando interno o externo, programa operable o archivo por lotes,", o los errores C1034 o LNK1104 al ejecutar el **cl** comando, a continuación, ya sea que no usa un símbolo del sistema, o algo no funciona correctamente con la instalación de Visual C++. Debe corregir este problema antes de continuar.  
  
     Si no se puede encontrar el programador acceso directo del símbolo del sistema, o si recibe un mensaje de error al escribir `cl`, a continuación, la instalación de Visual C++ puede tener un problema. Intente volver a instalar el componente de Visual C++ en Visual Studio, o vuelva a instalar Microsoft Visual C++ compilar Tools. No vaya a la sección siguiente hasta que esto funcione. Para obtener más información sobre la instalación y solución de problemas de Visual C++, vea [instalar Visual Studio](/visualstudio/install/install-visual-studio).  
  
    > [!NOTE]
    >  Según la versión de Windows en el equipo y la configuración de seguridad del sistema, es posible que deba haga clic en para abrir el menú contextual para el acceso directo del símbolo desarrollador y, a continuación, elija **ejecutar como administrador** para compilar y ejecutar el programa que se crea siguiendo este tutorial correctamente.  
  
### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Crear un archivo de código fuente de Visual C++ y compilarlo en la línea de comandos  
  
1.  En la ventana de símbolo del sistema para desarrolladores, escriba **md c:\hello** para crear un directorio y, a continuación, escriba **c:\hello cd** para cambiar a ese directorio. Este es el directorio que el archivo de origen y el programa compilado se crean en.  
  
2.  Escriba **notepad hello.cpp** en la ventana de símbolo del sistema.  
  
     Elija **Sí** cuando el Bloc de notas le pregunta si desea crear un archivo. Se abrirá una ventana de Bloc de notas en blanco, lista para que escriba el código en un archivo denominado hello.cpp.  
  
3.  En el Bloc de notas, escriba las siguientes líneas de código:  
  
    ```cpp  
    #include <iostream>  
    using namespace std;  
    void main()  
    {  
        cout << "Hello, world, from Visual C++!" << endl;  
    }  
    ```  
  
     Se trata de un programa muy sencillo que escribirá una línea de texto en la pantalla y, después, saldrá. Para minimizar los errores, copie este código y péguelo en el Bloc de notas.  
  
4.  No olvide guardar su trabajo. En el Bloc de notas, en el menú **Archivo** , elija **Guardar**.  
  
     Enhorabuena, ha creado un archivo de código fuente de Visual C++, hello.cpp, que está listo para compilar.  
  
5.  Vuelva a cambiar la ventana de símbolo del sistema para desarrolladores. Escriba **dir** en el símbolo del sistema para mostrar el contenido del directorio c:\hello. Debería ver el hello.cpp del archivo de origen en la lista de directorios, que es algo parecido a esto:  
  
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
  
     Las fechas y otros detalles variarán en su equipo. Si no ve el archivo de código fuente, hello.cpp, asegúrese de que ha cambiado en el directorio c:\hello creado y en el Bloc de notas, asegúrese de que había guarda el archivo de código fuente en este directorio. Además, asegúrese de que había guarda el código fuente con una extensión de nombre de archivo .cpp, no una extensión. txt.  
  
6.  En el símbolo del sistema, escriba `cl /EHsc hello.cpp` para compilar el programa.  
  
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
    >  Si se produce un error, como "'cl' no se reconoce como un comando interno o externo, programa operable o archivo por lotes,", o los errores C1034 o LNK1104, el símbolo del sistema para desarrolladores no está configurado correctamente. Para obtener información sobre cómo solucionar este problema, vuelva a la **abrir un símbolo del sistema para desarrolladores** sección.  
  
    > [!NOTE]
    >  Si recibe una advertencia o error del vinculador o compilador diferentes, revise el código fuente para corregir los errores, a continuación, guárdelo y vuelva a ejecutar el compilador. Para obtener información sobre errores concretos, use el cuadro de búsqueda en esta página MSDN para buscar el número de error.  
  
7.  Para ejecutar el programa hello.exe, en el símbolo del sistema, escriba `hello`.  
  
     El programa mostrará este texto y se cerrará:  
  
    ```Output  
    Hello, world, from Visual C++!  
    ```  
  
     Enhorabuena, simplemente ha compilado y ejecutar un programa de C++ mediante las herramientas de línea de comandos.  
  
## <a name="next-steps"></a>Pasos siguientes  
 En este ejemplo de "Hola, mundo" es tan sencillo como puede obtener un programa de C++. Programas de mundo real tienen archivos de encabezado y varios archivos de código fuente, vincular en bibliotecas, y realizar un trabajo útil.  
  
 Puede usar los pasos en este tutorial para crear su propio código de C++ en lugar de escribir el código de ejemplo mostrado. También puede crear muchos programas de ejemplo de código de C++ que encuentra en otra parte. Puede colocar el código fuente y compilar las aplicaciones en cualquier directorio de escritura. De forma predeterminada, el IDE de Visual Studio crea proyectos en la carpeta de documentos, en una subcarpeta de proyectos de una carpeta de Visual Studio con el nombre de la versión de Visual Studio.  
  
 Para compilar un programa que tiene varios archivos de código fuente, escríbalas todas en la línea de comandos, similar al siguiente:  
  
 `cl /EHsc file1.cpp file2.cpp file3.cpp`  
  
 La opción de la línea de comandos **/EHsc** le indica al compilador que habilite el control de excepciones de C++. Para obtener más información, consulte [/EH (Modelo de control de excepciones)](../build/reference/eh-exception-handling-model.md).  
  
 Al proporcionar varios archivos de origen como el siguiente, el compilador usa el primer archivo de entrada para crear el nombre del programa. En este caso, genera un programa llamado file1.exe. Para cambiar el nombre a program1.exe, agregue un [/out](../build/reference/out-output-file-name.md) opción del vinculador:  
  
 `cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`  
  
 Y para detectar errores de programación más automáticamente, se recomienda compilar utilizando la [/W3](../build/reference/compiler-option-warning-level.md) o [/W4](../build/reference/compiler-option-warning-level.md) opción de nivel de advertencia:  
  
 `cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`  
  
 El compilador, cl.exe, tiene muchas más opciones que puede aplicar para compilar, optimizar, depurar y analizar el código. ¿Para obtener una lista rápida, escriba **cl /?** en el símbolo del sistema para desarrolladores. También puede compilar y vincular por separado y aplicar las opciones del vinculador en escenarios de compilación más complejos. Para obtener más información sobre el compilador y las opciones del vinculador y uso, consulte [referencia de compilación de C/C ++](../build/reference/c-cpp-building-reference.md).  
  
 Puede usar NMAKE y MAKE (archivos) o archivos de proyecto y MSBuild para configurar y compilar proyectos más complejos en la línea de comandos. Para obtener más información sobre el uso de estas herramientas, consulte [referencia de NMAKE](../build/nmake-reference.md) y [MSBuild](../build/msbuild-visual-cpp.md).  
  
 Los lenguajes C y C++ son similares, pero no es el mismo. El compilador de Visual C++ usa una regla sencilla para determinar qué idioma que se usará cuando se compila el código. De forma predeterminada, el compilador de Visual C++ trata todos los archivos que finalizan en .c como código fuente de C, y todos los archivos que finalizan en .cpp como código fuente de C++. Para forzar al compilador que trate todos los archivos como C++, independientemente de la extensión de nombre de archivo, use la [/TC](../build/reference/tc-tp-tc-tp-specify-source-file-type.md) opción del compilador.  
  
 El compilador de Visual C++ incluye una biblioteca de tiempo de ejecución de C (CRT) generalmente compatible con el estándar ISO C99, pero no es totalmente compatible. En la mayoría de los casos, código portable se compile y ejecute según lo esperado. Visual C++ no admite algunos de los cambios de CRT en C11 ISO. Ciertas funciones de la biblioteca y los nombres de función POSIX están en desuso por el compilador de Visual C++. Se admiten las funciones, pero los nombres preferidos han cambiado. Para obtener más información, consulte [características de seguridad en CRT](../c-runtime-library/security-features-in-the-crt.md) y [C4996 de advertencia del compilador (nivel 3)](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Compilación de programas de C/C++](../build/building-c-cpp-programs.md)   
 [Opciones del compilador](../build/reference/compiler-options.md)