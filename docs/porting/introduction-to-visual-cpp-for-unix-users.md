---
title: "Introducci&#243;n a Visual C++ para los usuarios de UNIX | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "UNIX [C++]"
ms.assetid: 36108b31-e7fa-49a8-a1f7-7077fcbec873
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Introducci&#243;n a Visual C++ para los usuarios de UNIX
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tema proporciona información a los usuarios de UNIX que no estén familiarizados con [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] y deseen ser más productivos con [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)].  
  
## Introducción a la línea de comandos  
 Puede utilizar [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] desde la línea de comandos de manera similar a como utilizaría un entorno de línea de comandos de UNIX.  Debe realizar la compilación desde el símbolo del sistema con el compilador de línea de comandos de C y C\+\+ \(CL. \(EXE\) y las herramientas, incluyendo NMAKE. EXE, la versión de Microsoft de la utilidad de creación de UNIX.  
  
 En UNIX los comandos se instalan en una carpeta común, como\/usr\/bin.  En [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] las herramientas de línea de comandos se instalan en el directorio de instalación en VC\\bin \(en una instalación típica en Archivos de programa\\Microsoft Visual Studio 8\\VC\\bin\).  Para utilizar las herramientas de línea de comandos, ejecute vsvars32.bat, que se encuentra en el directorio de instalación en Common7\\Tools.  Esto agrega el directorio bin a la ruta de acceso y establece otras rutas de acceso necesarias para compilar programas de Visual C\+\+ desde la línea de comandos.  
  
> [!NOTE]
>  Si abre un símbolo del sistema con el **Símbolo de la línea de comandos de Visual Studio** desde el menú **Inicio**, se ejecuta vsvars32.bat.  
  
 Para aprovechar las características más potentes, como el depurador, la finalización de instrucciones, etc., deberá utilizar el entorno de desarrollo.  Para obtener más información, vea [Compilar en la línea de comandos](../build/building-on-the-command-line.md) y [Tutorial: Compilar un programa nativo de C\+\+ en la línea de comandos](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).  
  
## Depurar el código  
 Si usa la línea de comandos y ejecuta aplicaciones en la estación de trabajo de desarrollo, verá que se muestra un cuadro de diálogo para ejecutar el depurador [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] cuando el código encuentra una infracción de acceso de la memoria, una excepción no controlada u otros errores irrecuperables.  Si hace clic en **Aceptar**, se inicia el entorno de desarrollo de Visual Studio y el depurador se abre en el punto de error.  Es posible depurar las aplicaciones de esta manera y, en este caso, el código fuente solo estaría disponible si la compilación se realizó con el modificador [\/Z7, \/Zi, \/ZI \(Formato de la información de depuración\)](../build/reference/z7-zi-zi-debug-information-format.md).  Para obtener más información, vea [Depuración de código nativo](../Topic/Debugging%20Native%20Code.md) e [Utilizar el IDE de Visual Studio para desarrollo de escritorio de C\+\+](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
## Uso del entorno de desarrollo  
 Es más fácil utilizar el entorno de desarrollo para editar y compilar el código fuente en un *proyecto*.  Un proyecto es una colección de archivos de origen y archivos relacionados que se compilarán en una sola unidad, como una biblioteca o un ejecutable.  Un proyecto también contiene información sobre cómo se deben compilar los archivos.  La información sobre los proyectos se almacena en un archivo de proyecto con la extensión .prj.  
  
 Una aplicación consta de varias bibliotecas y ejecutables, cada uno de las cuales se haya compilado probablemente con un conjunto diferente de opciones del compilador o incluso en un lenguaje diferente y se almacenan en varios proyectos que forman parte de una sola *solución*.  Una solución es una abstracción para que un contenedor agrupe varios proyectos juntos.  La información sobre soluciones se almacena en un archivo de soluciones con la extensión .sln.  Para obtener más información, vea [PAVE: Managing Solutions and Projects](http://msdn.microsoft.com/es-es/7a50db22-d3cc-46f3-b648-ab7e0528e260) e [Utilizar el IDE de Visual Studio para desarrollo de escritorio de C\+\+](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
## Importar el código existente  
 Puede usar [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] para usar código existente que esté configurado para compilar con o sin un archivo Make y colocarlo en un proyecto [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  Para obtener más información, vea el **Asistente para crear proyectos a partir de archivos de código existentes**.  Para obtener más información, vea [Cómo: Crear un proyecto de C\+\+ a partir del código existente](../ide/how-to-create-a-cpp-project-from-existing-code.md).  
  
## Crear un proyecto nuevo  
 Puede crear nuevos proyectos en el entorno de desarrollo.  [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] proporciona numerosas plantillas que proporcionan código estándar para diversos proyectos comunes.  Puede usar los asistentes para aplicaciones para generar proyectos con esquemas de código para distintos tipos de aplicaciones.  
  
 Puede comenzar con un proyecto vacío mediante el **Asistente para aplicaciones de consola \(Win32\)**.  Seleccione la casilla **Proyecto vacío**.  A partir de este momento podrá agregar archivos nuevos y existentes al proyecto.  
  
 Al crear un proyecto, se le debe asignar un nombre.  De forma predeterminada, el nombre del proyecto es igual al nombre de la biblioteca de vínculos dinámicos \(DLL\) o del ejecutable que se compila a partir del proyecto.  Para obtener más información, vea [Crear soluciones y proyectos](../Topic/Creating%20Solutions%20and%20Projects.md).  
  
## Modificadores específicos de Microsoft  
 Visual C\+\+ contiene varias extensiones para el lenguaje de programación C\+\+ estándar.  Estas extensiones se utilizan para especificar atributos de clase de almacenamiento, convenciones de llamadas a función y direccionamiento con base, entre otros.  Para ver una lista con todas las extensiones de Visual C\+\+, vea [Modificadores específicos de Microsoft](../cpp/microsoft-specific-modifiers.md).  
  
 Puede deshabilitar todas las extensiones específicas de Microsoft C\+\+ utilizando la opción del compilador **\/Za**.  Esta opción se recomienda si desea escribir código para que se ejecute en varias plataformas.  Para obtener más información sobre la opción del compilador **\/Za**, vea [\/Za, \/Ze \(Deshabilitar extensiones de lenguaje\)](../build/reference/za-ze-disable-language-extensions.md).  Para obtener más información sobre la conformidad con Visual C\+\+, vea [Problemas de compatibilidad y conformidad en Visual C\+\+](../misc/compatibility-and-compliance-issues-in-visual-cpp.md).  
  
## Encabezados precompilados  
 Los compiladores de Microsoft C y C\+\+ ofrecen opciones para precompilar cualquier código de C o C\+\+, incluido el código en línea.  Usar esta función de rendimiento le permite compilar un cuerpo estable de código, almacenar el estado compilado del código en un archivo y, en las posteriores compilaciones, combinar el código precompilado con código que aun se esté desarrollando.  Cada compilación posterior se realizará más rápidamente porque no se tendrá que volver a compilar el código estable.  
  
 De forma predeterminada, todo el código precompilado se especifica en los archivos **stdafx.h** y **stdafx.cpp**.  El asistente **Nuevo proyecto** creará automáticamente estos archivos a menos que se anule la selección de la opción **Encabezado precompilado**.  Para obtener más información sobre encabezados precompilados, vea [Crear archivos de encabezado precompilados](../build/reference/creating-precompiled-header-files.md).  
  
## Secciones relacionadas  
 Para obtener más información, vea [Trasladar de UNIX a Win32](../porting/porting-from-unix-to-win32.md).  
  
## Vea también  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/es-es/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)