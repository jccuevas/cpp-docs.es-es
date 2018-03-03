---
title: Crear y administrar proyectos de Visual C++ | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c38f4c75a41de8b2f2b494941c6a52b1ff46fa4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="creating-and-managing-msbuild-based-visual-c-projects"></a>Crear y administrar proyectos basados en MSBuild de Visual C++
MSBuild es el sistema de compilación nativa para Visual C++ y generalmente es que mejor compilar sistema debe utilizar para aplicaciones UWP, así como aplicaciones de escritorio que utilizan bibliotecas MFC o ATL. MSBuild está totalmente integrado con el IDE de Visual Studio y el sistema del proyecto, pero también puede usarlo desde la línea de comandos. A partir de 2017 de Visual Studio, Visual C++ admite [CMake y otros sistemas de MSBuild no a través de la característica Abrir carpeta](non-msbuild-projects.md).

Un proyecto de MSBuild tiene un archivo de proyecto en formato XML (.vcxproj) que especifica todos los archivos y recursos necesitan para compilar el programa, así como otras opciones de configuración, por ejemplo la plataforma de destino (x 86, x64 o ARM) y si está creando un versión preliminar o versión de depuración del programa. Un proyecto (o muchos proyectos) se incluyen dentro de una *Solución*: por ejemplo, una solución podría contener varios proyectos de archivos DLL para Win32 y una única aplicación de consola Win32 que utilice dichos archivos DLL. Al compilar el proyecto, el motor de MSBuild consume el archivo de proyecto y genera el archivo ejecutable o cualquier otro resultado personalizado que se haya especificado.

Puede crear proyectos de Visual C++ eligiendo **archivo &#124; Nuevo &#124; Proyecto**, asegurándose de que Visual C++ esté seleccionado en el panel izquierdo y, a continuación, elija en la lista de plantillas de proyecto en el panel central. Al hacer clic en una plantilla, en muchos casos un asistente aparecerá que le permite establecer varias propiedades del proyecto antes de crea el proyecto. Puede ver y modificar las propiedades más adelante mediante el uso de páginas de propiedades del proyecto (**proyecto &#124; Propiedades de**).  
  
 También puede crear nuevos proyectos:  
  
-   elegir **archivo &#124; Nuevo &#124; Proyecto del código existente** y siga las indicaciones para agregar archivos de código fuente existentes. Esta opción funciona mejor con proyectos relativamente pequeños y simples, con un máximo de 25 archivos de código fuente con ninguna o pocas dependencias complejas.  
  
-   comenzando por un archivo Make y eligiendo la plantilla de proyecto de archivos Make en la pestaña General.  
  
-   crear un proyecto vacío (bajo la **General** ficha) y agregando manualmente archivos de código fuente, con el botón secundario en el nodo de proyecto en el Explorador de soluciones y elija **Agregar &#124; Elemento existente**.  
  
-   using the [Win32 Application Wizard](../windows/win32-application-wizard.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Tipos de proyecto de Visual C++](../ide/visual-cpp-project-types.md)  
 Describe los tipos de proyecto basado en MSBuild que están disponibles en Visual C++.  
  
 [Tipos de archivos creados para proyectos de Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)  
 Describe los tipos de archivos que se utilizan con distintos tipos de proyecto de MSBuild.  
  
 [Crear proyectos de escritorio con asistentes para aplicaciones](../ide/creating-desktop-projects-by-using-application-wizards.md)  
 Describe cómo usar los asistentes para crear proyectos con Visual C++.  
  
 [Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md)  
 Describe cómo usar páginas de propiedades y hojas de propiedades para especificar la configuración del proyecto.  
  
 [Agregar funcionalidad con los asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)  
 Describe cómo agregar al proyecto clases, métodos, variables y otros elementos para aportar más funcionalidad.  
  
 [Cómo: Organizar archivos de resultados de proyectos para la compilación](../ide/how-to-organize-project-output-files-for-builds.md)  
 Describe cómo organizar los archivos de salida del proyecto.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Compilación de programas de C/C++](../build/building-c-cpp-programs.md)  
 Ofrece vínculos a temas en los que se describe la compilación de programas desde la línea de comandos o desde el entorno de desarrollo integrado de Visual Studio.  
  
 [Referencias de Visual C++](http://msdn.microsoft.com/en-us/1ba03b5c-8229-4f63-b08c-6c12141d6ab1)  
 Contiene vínculos a temas en los que se describen las referencias de los lenguajes C y C++, las bibliotecas suministradas con Visual C++, el Modelo de objetos de extensibilidad de Visual C++ y Microsoft Macro Assembler (MASM).  
  
## <a name="see-also"></a>Vea también  
 [Visual Studio SDK](http://msdn.microsoft.com/vstudio/extend)
