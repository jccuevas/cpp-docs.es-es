---
title: "Resource Files (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "resources [Visual Studio]"
  - ".rc files"
  - "resource files"
  - "resource script files"
  - "resource script files, Win-32 based applications"
  - "resource script files, files updated when editing resources"
  - "resources [Visual Studio], types of resource files"
  - "rct files"
  - "resources [C++]"
  - "rc files"
  - "resource files, types of"
  - ".rct files"
  - "resource script files, unsupported types"
ms.assetid: 4d2b6fcc-07cf-4289-be87-83a60f69533c
caps.latest.revision: 18
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Resource Files (Visual Studio)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  Este material se aplica a aplicaciones de escritorio de Windows. Para información sobre los recursos de las aplicaciones [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)], vea [Definición de recursos de una aplicación](http://msdn.microsoft.com/es-es/476ea844-632c-4467-9ce3-966be1350dd4).  
>   
>  Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Puesto que los proyectos en los lenguajes de programación de .NET no usan archivos de script de recursos, los recursos deben abrirse desde el **Explorador de soluciones**. Se puede usar el [Editor de imágenes](../mfc/image-editor-for-icons.md) y el [Editor binario](../mfc/binary-editor.md) para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustado. Para información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 El término "archivo de recursos" puede hacer referencia a varios tipos de archivo, incluidos:  
  
-   El archivo de script de recursos \(.rc\) de un programa.  
  
-   Un archivo de plantilla de recursos \(.rct\).  
  
-   Un recurso individual existente como archivo independiente, como un archivo de mapa de bits, icono o cursor al que se hace referencia a partir de un archivo .rc.  
  
-   Un archivo de encabezado generado por el entorno de desarrollo, por ejemplo, Resource.h, al que se hace referencia a partir de un archivo .rc.  
  
 Los recursos también se pueden encontrar en [otros tipos de archivo](../windows/editable-file-types-for-resources.md) como archivos .exe, .dll y. res. Puede trabajar con recursos y archivos de recursos dentro del proyecto y con los que no forman parte de su proyecto actual. También puede trabajar con archivos de recursos que no se crearon en el entorno de desarrollo de Visual Studio. Por ejemplo, se puede:  
  
-   Trabajar con archivos de recursos anidados e incluidos condicionalmente.  
  
-   Actualizar recursos existentes o convertirlos al formato de Visual C\+\+.  
  
-   Importar o exportar recursos gráficos al archivo de recursos actual o desde él.  
  
-   Incluir identificadores compartidos o de solo lectura \(símbolos\) que no se pueden modificar por el entorno de desarrollo.  
  
-   Incluir recursos en el archivo ejecutable \(.exe\) que no requieran edición \(o que no quiera que se editen\) durante el proyecto actual, como los recursos que se comparten entre varios proyectos.  
  
-   Incluir tipos de recursos no admitidos en el entorno de desarrollo.  
  
 En esta sección se tratan los siguientes temas:  
  
-   [Creación de un archivo nuevo de script de recursos](../windows/how-to-create-a-resource-script-file.md)  
  
-   [Creación de un recurso nuevo](../windows/how-to-create-a-resource.md)  
  
-   [Visualización de recursos en un archivo de script de recursos](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)  
  
-   [Apertura de un archivo de script de recursos en formato de texto](../windows/how-to-open-a-resource-script-file-in-text-format.md)  
  
-   [Inclusión de recursos en tiempo de compilación](../Topic/How%20to:%20Include%20Resources%20at%20Compile%20Time.md)  
  
-   [Copia de recursos](../windows/how-to-copy-resources.md)  
  
-   [Uso de plantilla de recursos \(.rct\)](../Topic/How%20to:%20Use%20Resource%20Templates.md)  
  
-   [Importación y exportación de recursos](../windows/how-to-import-and-export-resources.md)  
  
-   [Tipos de archivos editables para recursos](../windows/editable-file-types-for-resources.md)  
  
-   [Archivos afectados al editar recursos](../Topic/Files%20Affected%20by%20Resource%20Editing.md)  
  
## Requisitos  
 Win32  
  
## Vea también  
 [Resource Editors](../mfc/resource-editors.md)   
 [Working with Resource Files](../mfc/working-with-resource-files.md)   
 [Menús y otros recursos](http://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)