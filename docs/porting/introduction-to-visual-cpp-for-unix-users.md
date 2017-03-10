---
title: "Introducción a Visual C++ para los usuarios de UNIX | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- UNIX [C++]
ms.assetid: 36108b31-e7fa-49a8-a1f7-7077fcbec873
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7c75629d56e6d8e5291b7d1f7cca9995ab9a50da
ms.openlocfilehash: d8515fc613f95ae5d6395e33b49482488bcc488d
ms.lasthandoff: 02/24/2017

---
# <a name="introduction-to-visual-c-for-unix-users"></a>Introducción a Visual C++ para los usuarios de UNIX
Este tema proporciona información a los usuarios de UNIX que no estén familiarizados con [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] y deseen ser más productivos con [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)].  
  
## <a name="getting-started-on-the-command-line"></a>Introducción a la línea de comandos  
 Puede utilizar [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] desde la línea de comandos de manera similar a como utilizaría un entorno de línea de comandos de UNIX. Debe realizar la compilación desde el símbolo del sistema con el compilador de línea de comandos de C y C++ (CL. (EXE) y las herramientas, incluyendo NMAKE. EXE, la versión de Microsoft de la utilidad de creación de UNIX.  
  
 En UNIX los comandos se instalan en una carpeta común, como/usr/bin. En [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] las herramientas de línea de comandos se instalan en el directorio de instalación en VC\bin (en una instalación típica en Archivos de programa\Microsoft Visual Studio 8\VC\bin). Para utilizar las herramientas de línea de comandos, ejecute vsvars32.bat, que se encuentra en el directorio de instalación en Common7\Tools. Esto agrega el directorio bin a la ruta de acceso y establece otras rutas de acceso necesarias para compilar programas de Visual C++ desde la línea de comandos. Para más información, vea [Compilar en la línea de comandos](../build/building-on-the-command-line.md) y [Tutorial: Compilar un programa nativo de C++ en la línea de comandos](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).  
  
> [!NOTE]
>  Si abre un símbolo del sistema con el **Símbolo de la línea de comandos de Visual Studio** desde el menú **Inicio**, se ejecuta vsvars32.bat.  
  
 Para aprovechar características más potentes, como el depurador de Visual Studio, la finalización de instrucciones, etc., tiene que usar el entorno de desarrollo.  
  
## <a name="debugging-your-code"></a>Depurar el código  
 Si usa la línea de comandos y ejecuta aplicaciones en la estación de trabajo de desarrollo, verá que se muestra un cuadro de diálogo para ejecutar el depurador [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] cuando el código encuentra una infracción de acceso de la memoria, una excepción no controlada u otros errores irrecuperables. Si hace clic en **Aceptar**, se inicia el entorno de desarrollo de Visual Studio y el depurador se abre en el punto de error. Es posible depurar las aplicaciones de esta manera, en cuyo caso, el código fuente solo estaría disponible si la compilación se realizara con el modificador [/Z7, /Zi, /ZI (formato de información de depuración)](../build/reference/z7-zi-zi-debug-information-format.md). Para más información, vea [Depuración de código nativo](/visualstudio/debugger/debugging-native-code) y [Utilizar el IDE de Visual Studio para desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
## <a name="using-the-development-environment"></a>Uso del entorno de desarrollo  
 Es más fácil usar el entorno de desarrollo para editar y compilar el código fuente en un *proyecto*. Un proyecto es una colección de archivos de origen y archivos relacionados que se compilarán en una sola unidad, como una biblioteca o un ejecutable. Un proyecto también contiene información sobre cómo se deben compilar los archivos. La información sobre los proyectos se almacena en un archivo de proyecto con la extensión .prj.  
  
 Una aplicación que consta de varias bibliotecas y ejecutables, cada uno compilado probablemente con un conjunto diferente de opciones del compilador o incluso en un lenguaje diferente, que se almacenan en varios proyectos que forman parte de una sola *solución*. Una solución es una abstracción para que un contenedor agrupe varios proyectos juntos. La información sobre soluciones se almacena en un archivo de soluciones con la extensión .sln. Para más información, vea [Soluciones y proyectos en Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio) y [Utilizar el IDE de Visual Studio para desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
## <a name="importing-your-existing-code"></a>Importar el código existente  
 Puede usar [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] para usar código existente que esté configurado para compilar con o sin un archivo Make y colocarlo en un proyecto [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]. Para más información, vea **Asistente para crear nuevo proyecto de archivos de código fuente existentes**. Para más información, vea [Cómo: Crear un proyecto de C++ a partir del código existente](../ide/how-to-create-a-cpp-project-from-existing-code.md).  
  
## <a name="creating-a-new-project"></a>Crear un proyecto nuevo  
 Puede crear nuevos proyectos en el entorno de desarrollo. [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] proporciona numerosas plantillas que proporcionan código estándar para diversos proyectos comunes. Puede usar los asistentes para aplicaciones para generar proyectos con esquemas de código para distintos tipos de aplicaciones.  
  
 Puede comenzar con un proyecto vacío mediante el **Asistente para aplicaciones de consola (Win32)**. Active la casilla **Proyecto vacío**. A partir de este momento podrá agregar archivos nuevos y existentes al proyecto.  
  
 Al crear un proyecto, se le debe asignar un nombre. De forma predeterminada, el nombre del proyecto es igual al nombre de la biblioteca de vínculos dinámicos (DLL) o del ejecutable que se compila a partir del proyecto. Para más información, vea [Crear soluciones y proyectos](/visualstudio/ide/creating-solutions-and-projects).  
  
## <a name="microsoft-specific-modifiers"></a>Modificadores específicos de Microsoft  
 Visual C++ contiene varias extensiones para el lenguaje de programación C++ estándar. Estas extensiones se utilizan para especificar atributos de clase de almacenamiento, convenciones de llamadas a función y direccionamiento con base, entre otros. Para obtener una lista completa de todas las extensiones de Visual C++, vea [Modificadores específicos de Microsoft](../cpp/microsoft-specific-modifiers.md).  
  
 Puede deshabilitar todas las extensiones específicas de Microsoft para C++ con la opción del compilador **/Za**. Esta opción se recomienda si desea escribir código para que se ejecute en varias plataformas. Para más información sobre la opción del compilador **/Za**, vea [/Za, /Ze (Deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md). Para más información sobre la conformidad de Visual C++, vea [Comportamiento no estándar](../cpp/nonstandard-behavior.md).  
  
## <a name="precompiled-headers"></a>Encabezados precompilados  
 Los compiladores de Microsoft C y C++ ofrecen opciones para precompilar cualquier código de C o C++, incluido el código en línea. Usar esta función de rendimiento le permite compilar un cuerpo estable de código, almacenar el estado compilado del código en un archivo y, en las posteriores compilaciones, combinar el código precompilado con código que aun se esté desarrollando. Cada compilación posterior se realizará más rápidamente porque no se tendrá que volver a compilar el código estable.  
  
 De forma predeterminada, todo el código precompilado se especifica en los archivos **stdafx.h** y **stdafx.cpp**. El asistente **Nuevo proyecto** creará automáticamente estos archivos, a menos que se desactive la opción **Encabezado precompilado**. Para más información sobre los encabezados precompilados, vea [Crear archivos de encabezado precompilados](../build/reference/creating-precompiled-header-files.md).  
  
## <a name="related-sections"></a>Secciones relacionadas  
 Para más información, vea [Trasladar de UNIX a Win32](../porting/porting-from-unix-to-win32.md).  
  
## <a name="see-also"></a>Vea también  
 [Paseo guiado por Visual C++](http://msdn.microsoft.com/en-us/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)
