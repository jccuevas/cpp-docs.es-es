---
title: Creación y administración de proyectos de Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vcprojects
- creatingmanagingVC
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, creating
- Visual C++ projects, creating
- projects [C++], creating
- Visual C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f56ee748738cd67199348c93272a9cd2ed564e2c
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685704"
---
# <a name="creating-and-managing-msbuild-based-visual-c-projects"></a>Creación y administración de proyectos de Visual C++ basados en MSBuild
MSBuild es el sistema de compilación nativo para Visual C++ y, generalmente, es el mejor para las aplicaciones para UWP, así como para las aplicaciones de escritorio que usan bibliotecas de MFC o ATL. MSBuild está totalmente integrado con el IDE y el sistema de proyectos de Visual Studio, pero también se puede usar desde la línea de comandos. A partir de Visual Studio 2017, Visual C++ admite [CMake y otros sistemas que no son MSBuild a través de la característica Abrir carpeta](non-msbuild-projects.md).

Un proyecto basado en MSBuild tiene un archivo de proyecto en formato XML (.vcxproj) en el que se especifican todos los archivos y los recursos necesarios para compilar el programa, así como otras opciones de configuración, como la plataforma de destino (x86, x64 o ARM) y si se está creando una versión de lanzamiento o de depuración del programa. Un proyecto (o muchos proyectos) se incluyen dentro de una *Solución*: por ejemplo, una solución podría contener varios proyectos de archivos DLL para Win32 y una única aplicación de consola Win32 que utilice dichos archivos DLL. Al compilar el proyecto, el motor de MSBuild consume el archivo de proyecto y genera el archivo ejecutable o cualquier otro resultado personalizado que se haya especificado.

Puede crear proyectos de Visual C++ si selecciona **Archivo &#124; Nuevo &#124; Proyecto**, asegurándose de que Visual C++ esté seleccionado en el panel de la izquierda y, después, selecciona una de las plantillas de la lista de plantillas de proyecto del panel central. En muchos casos, al hacer clic en una plantilla, se mostrará un asistente que permite establecer varias propiedades del proyecto antes de crearlo. Estas propiedades se pueden ver y modificar más adelante mediante las páginas de propiedades del proyecto (**Proyecto &#124; Propiedades**).  
  
 También se pueden crear proyectos si:  
  
-   se selecciona **Archivo &#124; Nuevo &#124; Proyecto a partir de código existente** y se siguen las indicaciones para agregar los archivos de código fuente existentes. Esta opción funciona mejor con proyectos relativamente pequeños y simples, con un máximo de 25 archivos de código fuente con ninguna o pocas dependencias complejas.  
  
-   comenzando por un archivo Make y eligiendo la plantilla de proyecto de archivos Make en la pestaña General.  
  
-   se crea un proyecto vacío (bajo la pestaña **General**) y se agregan manualmente los archivos de código fuente haciendo clic con el botón derecho en el nodo de proyecto en el Explorador de soluciones y seleccionando **Agregar &#124; Elemento existente**.  
  
-   using the [Win32 Application Wizard](../windows/win32-application-wizard.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Tipos de proyecto de Visual C++](../ide/visual-cpp-project-types.md)  
 Describe los tipos de proyecto basados en MSBuild que están disponibles en Visual C++.  
  
 [Tipos de archivos creados para proyectos de Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)  
 Describe los tipos de archivos que se usan con distintos tipos de proyecto de MSBuild.  
  
 [Crear proyectos de escritorio con asistentes para aplicaciones](../ide/creating-desktop-projects-by-using-application-wizards.md)  
 Describe cómo usar los asistentes para crear proyectos con Visual C++.  
  
 [Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md)  
 Describe cómo usar páginas de propiedades y hojas de propiedades para especificar la configuración del proyecto.  
  
 [Agregar funcionalidad con los Asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)  
 Describe cómo agregar al proyecto clases, métodos, variables y otros elementos para aportar más funcionalidad.  
  
 [Cómo: Organizar archivos de resultados de proyectos para la compilación](../ide/how-to-organize-project-output-files-for-builds.md)  
 Describe cómo organizar los archivos de salida del proyecto.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Compilación de programas de C/C++](../build/building-c-cpp-programs.md)  
 Ofrece vínculos a temas en los que se describe la compilación de programas desde la línea de comandos o desde el entorno de desarrollo integrado de Visual Studio.  
  
## <a name="see-also"></a>Vea también  
 [Visual Studio SDK](https://msdn.microsoft.com/vstudio/extend)
