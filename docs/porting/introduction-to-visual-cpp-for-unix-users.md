---
title: Introducción a los C++ usuarios de Microsoft para UNIX
ms.date: 10/23/2019
helpviewer_keywords:
- UNIX [C++]
ms.assetid: 36108b31-e7fa-49a8-a1f7-7077fcbec873
ms.openlocfilehash: 791c513553acbd300204746ae1e1dddf7a3ae5c4
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626999"
---
# <a name="introduction-to-microsoft-c-for-unix-users"></a>Introducción a los C++ usuarios de Microsoft para UNIX

En este tema se proporciona información para los usuarios de todos los tipos de UNIX que son nuevos en Visual Studio y desean C++ ser productivos con desde la línea de comandos o mediante Visual Studio. Puede usar Visual Studio con el compilador de Microsoft C++ para tener como destino Windows. También puede usar el IDE de Visual Studio con GCC o Clang en entornos UNIX como equipos remotos de Linux, MinGW-W64 y subsistema de Windows para Linux. Para usar C++ en Visual Studio, debe estar instalado el **desarrollo de escritorio con C++**  carga de trabajo. Abra el Instalador de Visual Studio para instalar la carga de trabajo o agregar o quitar componentes opcionales. Instale también el **desarrollo de Linux C++ con** la carga de trabajo si va a tener como destino un equipo Linux remoto. Para el desarrollo de Android o iOS, instale el **desarrollo C++ para dispositivos móviles con** la carga de trabajo.

## <a name="getting-started-on-the-command-line"></a>Introducción a la línea de comandos

Puede usar el compilador de Microsoft C++ desde la línea de comandos de forma similar a como se haría con un entorno de línea de comandos de Unix. Debe realizar la compilación desde el símbolo del sistema con el compilador de línea de comandos de C y C++ (CL.EXE), el enlazador (LINK.EXE) y otras herramientas, incluyendo NMAKE. EXE, la versión de Microsoft de la utilidad de creación de UNIX.

En UNIX los comandos se instalan en una carpeta común, como/usr/bin. En Visual Studio, las herramientas de línea de comandos se instalan en el directorio de instalación de Visual Studio, en el subdirectorio VC\bin y sus subdirectorios. A diferencia de UNIX, estas herramientas no están disponibles en una simple ventana del símbolo del sistema. Para usar las herramientas de línea de comandos, debe usar un símbolo del sistema para desarrolladores especial que configure la ruta de acceso y otras variables de entorno C++ necesarias para compilar programas. Para más información, vea [Compilar código de C o C++ en la línea de comandos](../build/building-on-the-command-line.md) y [Tutorial: Compilar un programa nativo de C++ en la línea de comandos](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).

## <a name="debugging-your-code"></a>Depurar el código

Puede usar el depurador de Visual Studio para C++ proyectos de Microsoft desde la línea de comandos o desde el IDE. Compile con el modificador [/Z7,/Zi,/Zi (formato de la información de depuración)](../build/reference/z7-zi-zi-debug-information-format.md) para habilitar la ejecución paso a paso de los orígenes. Para más información, vea [Depuración de código nativo](/visualstudio/debugger/debugging-native-code) y [Utilizar el IDE de Visual Studio para desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

En el caso de los programas compilados con GCC o Clang, Visual Studio invoca GDB, LLDB o cualquier depurador personalizado que especifique.

## <a name="visual-studio-project-system"></a>Sistema de proyectos de Visual Studio

El sistema del proyecto de Visual Studio se denomina MSBuild. Utiliza archivos de proyecto en formato XML. C++ los archivos de proyecto tienen la extensión. vcxproj. Una aplicación que consta de varias bibliotecas y ejecutables, cada uno compilado probablemente con un conjunto diferente de opciones del compilador o incluso en un lenguaje diferente, que se almacenan en varios proyectos que forman parte de una sola *solución*. Una solución es una abstracción para que un contenedor agrupe varios proyectos juntos. La información sobre soluciones se almacena en un archivo de soluciones con la extensión .sln. Para más información, vea [Soluciones y proyectos en Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio) y [Utilizar el IDE de Visual Studio para desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md). En el menú principal, elija **archivo** > **nuevo** > **proyecto** para ver las plantillas de proyecto de Visual Studio disponibles.

A partir de Visual Studio 2017, se agrega compatibilidad con proyectos de CMake, así como opciones para usar el C++ compilador de Microsoft con cualquier sistema de compilación arbitrario o con una carpeta de archivos de código fuente y sin archivos de proyecto. Para obtener más información, consulte [CMake Projects in Visual Studio](../build/cmake-projects-in-visual-studio.md) y [Open folder Projects in Visual Studio](../build/open-folder-projects-cpp.md).

## <a name="microsoft-specific-modifiers"></a>Modificadores específicos de Microsoft

El Compilador de Microsoft C++ implementa varias extensiones para el lenguaje de programación de C++ que permiten la programación en sistemas operativos Windows. Estas extensiones se utilizan para especificar atributos de clase de almacenamiento, convenciones de llamadas a función y direccionamiento con base, entre otros. Para obtener una lista completa de todas las extensiones de C++ admitidas, vea [Modificadores específicos de Microsoft](../cpp/microsoft-specific-modifiers.md).

Puede deshabilitar todas las extensiones específicas de Microsoft C++ utilizando la opción del compilador `/Za`. Esta opción se recomienda si desea escribir código para que se ejecute en varias plataformas. Para más información sobre la opción del compilador `/Za`, vea [/Za, /Ze (Deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md). Para obtener más información C++ sobre la conformidad del compilador, vea [tabla de conformidad de lenguaje de C++ Microsoft](../overview/visual-cpp-language-conformance.md) y comportamiento no [estándar](../cpp/nonstandard-behavior.md).

## <a name="precompiled-headers"></a>Encabezados precompilados

Los compiladores de Microsoft C y C++ ofrecen opciones para precompilar cualquier código de C o C++, incluido el código en línea. Usar esta función de rendimiento le permite compilar un cuerpo estable de código, almacenar el estado compilado del código en un archivo y, en las posteriores compilaciones, combinar el código precompilado con código que aun se esté desarrollando. Cada compilación posterior se realizará más rápidamente porque no se tendrá que volver a compilar el código estable.

De forma predeterminada, todo el código precompilado se especifica en los archivos *pch.h* y *pch.cpp* (*stdafx.h* y *stdafx.cpp* en Visual Studio 2017 y versiones anteriores). Para más información sobre los encabezados precompilados, vea [Crear archivos de encabezado precompilados](../build/creating-precompiled-header-files.md).

## <a name="related-sections"></a>Secciones relacionadas

Para obtener más información, consulte [ejecutar programas de Linux en Windows](../porting/porting-from-unix-to-win32.md).

## <a name="see-also"></a>Vea también

[Proyectos y sistemas de compilación](../build/projects-and-build-systems-cpp.md)
