---
title: Compilar proyectos de C++ en Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++ projects, building
- projects [C++], building
- builds [C++], about building in Visual Studio
ms.assetid: 9e8bc1a2-bb17-4951-937a-c757ed88d2d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a7008e7fe670471301968482fbd4c6c758f0ff5e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="building-c-projects-in-visual-studio"></a>Compilar proyectos de C++ en Visual Studio
En el entorno de desarrollo integrado (IDE) de Visual Studio, hay varias formas de compilar una solución completa o solo uno de sus proyectos. También puede modificar la configuración de compilación y especificar pasos de compilación personalizada para que el proceso de desarrollo sea más eficiente.  
  
 Para crear una solución que esté abierta en Visual Studio y seleccionada en **el Explorador de soluciones**, puede:  
  
-   En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
-   O bien, en **el Explorador de soluciones**, abra el menú contextual de la solución y, a continuación, elija **generar solución**.  
  
-   O bien, presione F7 (es el método abreviado de teclado predeterminado de la configuración del desarrollo en C/C++).  
  
-   O bien, en la [ventana de comandos](/visualstudio/ide/reference/command-window) (en la barra de menús, elija **vista**, **otras ventanas**, **ventana de comandos**), escriba `Build.BuildSolution`.  
  
-   O bien, en la [inicio rápido](/visualstudio/ide/reference/quick-launch-environment-options-dialog-box) cuadro, escriba `build build solution`.  
  
 Para compilar un proyecto que está seleccionado en **el Explorador de soluciones**, puede:  
  
-   En la barra de menús, elija **generar**, **generar \<nombre del proyecto >**.  
  
-   O bien, en **el Explorador de soluciones**, abra el menú contextual para el proyecto y, a continuación, elija **generar**.  
  
-   O bien, en la ventana de comandos (en la barra de menús, elija **vista**, **otras ventanas**, **ventana de comandos**), escriba `Build.BuildOnlyProject`.  
  
-   O bien, en el cuadro Inicio rápido, escriba `build project only build only <project name>`.  
  
 Al compilar una aplicación de Visual C++ en Visual Studio, puede modificar gran parte de la configuración de la compilación en el cuadro de diálogo Páginas de propiedades del proyecto. Para obtener información sobre cómo establecer propiedades del proyecto, consulte [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).  
  
 Para obtener un ejemplo sobre cómo usar el IDE para crear, compilar y depurar un proyecto de C++, vea [Tutorial: explorar el IDE de Visual Studio con C++](/visualstudio/ide/getting-started-with-cpp-in-visual-studio). Para obtener un ejemplo sobre cómo usar el IDE para compilar un C + / proyecto CLR, vea [Tutorial: compilar un programa de C++ orientado a CLR en Visual Studio](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md). Para obtener un ejemplo sobre cómo usar el IDE para crear una aplicación de Windows en tiempo de ejecución, consulte [crear la primera aplicación de Windows Runtime con C++](http://msdn.microsoft.com/library/windows/apps/hh974580.aspx).  
  
 Para más información sobre cómo compilar, modificar la configuración de compilación y especificar pasos de compilación personalizada, consulte los siguientes artículos.  
  
## <a name="in-this-section"></a>En esta sección  
 [Descripción de los pasos de compilación personalizada y los eventos de compilación](../ide/understanding-custom-build-steps-and-build-events.md)  
 Describe cómo personalizar el proceso de compilación en el entorno de desarrollo integrado.  
  
 [Macros comunes para propiedades y comandos de compilación](../ide/common-macros-for-build-commands-and-properties.md)  
 Presenta una lista de macros que puede usar donde se aceptan cadenas.  
  
 [Compilar proyectos externos](../ide/building-external-projects.md)  
 Examina la compilación de proyectos que utilizan instalaciones de fuera del entorno de desarrollo integrado.  
  
 [Archivos de proyecto](../ide/project-files.md)  
 Presenta la estructura XML de un archivo .vcxproj.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Cuadro de diálogo de VC ++ directorios, proyectos, opciones](vcpp-directories-property-page.md)  
 (Solo para proyectos de MSBuild) Describe cómo modificar la ruta de acceso de búsqueda de los archivos ejecutables e incluir archivos, archivos de biblioteca y archivos de código fuente durante una compilación.  
  
 [Compilar y generar en Visual Studio](/visualstudio/ide/compiling-and-building-in-visual-studio)  
 Proporciona información sobre la compilación en Visual Studio.  
  
 [Compilación de programas de C/C++](../build/building-c-cpp-programs.md)  
 Ofrece vínculos a temas en los que se describe la compilación de programas desde la línea de comandos o desde el entorno de desarrollo integrado de Visual Studio.  
  
 [Referencia de compilación de C/C++](../build/reference/c-cpp-building-reference.md)  
 Incluye vínculos a una introducción a la compilación de programas en C++, opciones del compilador y el enlazador y herramientas de compilación adicionales.  
  
 [Actualizar proyectos desde versiones anteriores de Visual C++](../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
 Proporciona vínculos a temas que describen los problemas de actualización de su proyecto de C++ para las versiones más recientes de las herramientas del compilador.  
  
[Guía de migración y actualización de Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)  
  Información detallada sobre cómo actualizar las aplicaciones de C++ que se crearon en versiones anteriores de Visual Studio y también cómo migrar las aplicaciones que se crearon con herramientas distintas a Visual Studio.  
  
## <a name="see-also"></a>Vea también  
 [Aplicaciones de Windows universales (C++)](../windows/universal-windows-apps-cpp.md)