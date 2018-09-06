---
title: Introducción a Visual C++ para los usuarios de UNIX | Microsoft Docs
ms.custom: ''
ms.date: 09/01/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- UNIX [C++]
ms.assetid: 36108b31-e7fa-49a8-a1f7-7077fcbec873
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d5789e353a6e15d4da3f5754d9d4d91821359d14
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42578322"
---
# <a name="introduction-to-visual-c-for-unix-users"></a>Introducción a Visual C++ para los usuarios de UNIX

En este tema se proporciona información para los usuarios de UNIX que no estén familiarizados con Visual Studio y quieran obtener una mayor productividad con C++ y el entorno de desarrollo integrado (IDE) de Visual Studio.
  
## <a name="getting-started-on-the-command-line"></a>Introducción a la línea de comandos  

Puede usar el Compilador de Microsoft Visual C++ desde la línea de comandos de manera similar a como usaría un entorno de línea de comandos de UNIX. Debe realizar la compilación desde el símbolo del sistema con el compilador de línea de comandos de C y C++ (CL.EXE), el enlazador (LINK.EXE) y otras herramientas, incluyendo NMAKE. EXE, la versión de Microsoft de la utilidad de creación de UNIX.  
  
En UNIX los comandos se instalan en una carpeta común, como/usr/bin. En Visual Studio, las herramientas de línea de comandos se instalan en el directorio de instalación de Visual Studio, en el subdirectorio VC\bin y sus subdirectorios. A diferencia de UNIX, estas herramientas no están disponibles en una simple ventana del símbolo del sistema. Para usar las herramientas de línea de comandos, use un acceso directo del símbolo del sistema para desarrolladores, o ejecute un archivo de comandos para desarrolladores como vcvarsall.bat. Esto permite configurar la ruta de acceso y otras variables de entorno necesarias para compilar programas de C++ desde la línea de comandos. Para más información, vea [Compilar código de C o C++ en la línea de comandos](../build/building-on-the-command-line.md) y [Tutorial: Compilar un programa nativo de C++ en la línea de comandos](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).  
  
Para abrir un acceso directo del símbolo del sistema para desarrolladores, escriba *símbolo del sistema para desarrolladores* en el control de búsqueda del escritorio y elija el resultado **Símbolo del sistema para desarrollares** correspondiente a su versión de Visual Studio. Para elegir un símbolo del sistema para desarrolladores que esté preconfigurado para un host determinado y la arquitectura de destino, abra el menú **Inicio** (el icono de Windows en la esquina del escritorio) y desplácese a la carpeta de su versión de Visual Studio, como **Visual Studio 2017**. Abra la carpeta y elija el acceso directo del símbolo del sistema para el host y la arquitectura de destino que prefiera.
  
Use el IDE de Visual Studio para aprovechar la eficacia de características como, por ejemplo, el depurador de Visual Studio, la finalización de instrucciones y la búsqueda de código de IntelliSense, los diseñadores visuales y la administración de proyectos.  
  
## <a name="debugging-your-code"></a>Depurar el código  

Si usa la línea de comandos y ejecuta aplicaciones en la estación de trabajo de desarrollo, verá que se muestra un cuadro de diálogo para ejecutar el depurador de Visual Studio cuando el código encuentra una infracción de acceso de la memoria, una excepción no controlada u otros errores irrecuperables. Si hace clic en **Aceptar**, se inicia el entorno de desarrollo de Visual Studio y el depurador se abre en el punto de error. Es posible depurar las aplicaciones de esta manera, en cuyo caso, el código fuente solo estaría disponible si la compilación se realizara con el modificador [/Z7, /Zi, /ZI (formato de información de depuración)](../build/reference/z7-zi-zi-debug-information-format.md). Para más información, vea [Depuración de código nativo](/visualstudio/debugger/debugging-native-code) y [Utilizar el IDE de Visual Studio para desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
## <a name="using-the-development-environment"></a>Uso del entorno de desarrollo  

Es más fácil usar el entorno de desarrollo para editar y compilar el código fuente en un *proyecto*. Un proyecto es una colección de archivos de origen y archivos relacionados que se compilarán en una sola unidad, como una biblioteca o un ejecutable. Un proyecto también contiene información sobre cómo se deben compilar los archivos. La información sobre los proyectos se almacena en un archivo de proyecto con la extensión .prj.  
  
Una aplicación que consta de varias bibliotecas y ejecutables, cada uno compilado probablemente con un conjunto diferente de opciones del compilador o incluso en un lenguaje diferente, que se almacenan en varios proyectos que forman parte de una sola *solución*. Una solución es una abstracción para que un contenedor agrupe varios proyectos juntos. La información sobre soluciones se almacena en un archivo de soluciones con la extensión .sln. Para más información, vea [Soluciones y proyectos en Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio) y [Utilizar el IDE de Visual Studio para desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
## <a name="importing-your-existing-code"></a>Importar el código existente 
 
Puede usar el compilador de C++ para compilar código existente que se haya configurado para compilaciones con o sin archivos Make y usarlo en un proyecto de Visual Studio. Para más información, vea [Cómo: Crear un proyecto de C++ a partir del código existente](../ide/how-to-create-a-cpp-project-from-existing-code.md).  
  
## <a name="creating-a-new-project"></a>Crear un proyecto nuevo  

Puede crear nuevos proyectos en el entorno de desarrollo. Visual Studio proporciona numerosas plantillas que ofrecen código estándar para diversos proyectos comunes. Puede usar los asistentes para aplicaciones para generar proyectos con esquemas de código para distintos tipos de aplicaciones.  
  
Puede comenzar con un proyecto vacío mediante el **Asistente para aplicaciones de consola (Win32)**. Active la casilla **Proyecto vacío**. A partir de este momento podrá agregar archivos nuevos y existentes al proyecto.  
  
Al crear un proyecto, se le debe asignar un nombre. De forma predeterminada, el nombre del proyecto es igual al nombre de la biblioteca de vínculos dinámicos (DLL) o del ejecutable que se compila a partir del proyecto. Para más información, vea [Crear soluciones y proyectos](/visualstudio/ide/creating-solutions-and-projects).  
  
## <a name="microsoft-specific-modifiers"></a>Modificadores específicos de Microsoft  

El Compilador de Microsoft Visual C++ implementa varias extensiones para el lenguaje de programación de C++ que permiten la programación en sistemas operativos Windows. Estas extensiones se utilizan para especificar atributos de clase de almacenamiento, convenciones de llamadas a función y direccionamiento con base, entre otros. Para obtener una lista completa de todas las extensiones de C++ admitidas, vea [Modificadores específicos de Microsoft](../cpp/microsoft-specific-modifiers.md).  
  
Puede deshabilitar todas las extensiones específicas de Microsoft C++ utilizando la opción del compilador `/Za`. Esta opción se recomienda si desea escribir código para que se ejecute en varias plataformas. Para más información sobre la opción del compilador `/Za`, vea [/Za, /Ze (Deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md). Para obtener más información sobre el cumplimiento del Compilador de Microsoft Visual C++, consulte [Conformidad del lenguaje Visual C++](../visual-cpp-language-conformance.md) y [Comportamiento no estándar](../cpp/nonstandard-behavior.md).  
  
## <a name="precompiled-headers"></a>Encabezados precompilados  

Los compiladores de Microsoft C y C++ ofrecen opciones para precompilar cualquier código de C o C++, incluido el código en línea. Usar esta función de rendimiento le permite compilar un cuerpo estable de código, almacenar el estado compilado del código en un archivo y, en las posteriores compilaciones, combinar el código precompilado con código que aun se esté desarrollando. Cada compilación posterior se realizará más rápidamente porque no se tendrá que volver a compilar el código estable.  
  
De forma predeterminada, todo el código precompilado se especifica en los archivos stdafx.h y stdafx.cpp. El asistente **Nuevo proyecto** creará automáticamente estos archivos, a menos que se desactive la opción **Encabezado precompilado**. Para más información sobre los encabezados precompilados, vea [Crear archivos de encabezado precompilados](../build/reference/creating-precompiled-header-files.md).  
  
## <a name="related-sections"></a>Secciones relacionadas  

Para más información, vea [Trasladar de UNIX a Win32](../porting/porting-from-unix-to-win32.md).  
  
## <a name="see-also"></a>Vea también  

[Compilación de programas de C/C++](../build/building-c-cpp-programs.md)