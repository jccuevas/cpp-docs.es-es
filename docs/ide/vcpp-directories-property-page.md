---
title: "Directorios de VC++ (P&#225;gina de propiedades) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCDirectories.IncludePath"
  - "VC.Project.VCDirectories.ReferencePath"
  - "VC.Project.VCDirectories.SourcePath"
  - "VC.Project.VCDirectories.LibraryWPath"
  - "VC.Project.VCDirectories.ExecutablePath"
  - "VC.Project.VCDirectories.LibraryPath"
  - "VS.ToolsOptionsPages.Projects.VCDirectories"
  - "VC.Project.VCDirectories.ExcludePath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Directorios de VC++ (Página de propiedades)"
ms.assetid: 428eeef6-f127-4271-b3ea-0ae6f2c3d624
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Directorios de VC++ (P&#225;gina de propiedades)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica los directorios que desea que Visual Studio utilice para compilar un proyecto.  Para tener acceso a esta página de propiedades, en el **Explorador de soluciones**, abra el menú contextual del proyecto y elija **Propiedades**; después, en el panel izquierdo del cuadro de diálogo **Páginas de propiedades**, expanda **Propiedades de configuración** y seleccione **Directorios de VC\+\+**.  
  
 Cuando se utiliza Visual Studio para crear un proyecto, este hereda ciertos directorios.  Muchos de ellos se proporcionan como macros.  Para examinar el valor actual de una macro, en el panel derecho de la página de **Directorios de VC\+\+**, seleccione una fila \(por ejemplo, **Directorios de archivos de inclusión**\), elija el botón de flecha abajo situado a la derecha, elija **Editar** y a continuación, en el cuadro de diálogo que aparece, elija el botón **Macros**.  Para obtener más información, vea estas entradas de blog: [Directorios de VC\+\+](http://blogs.msdn.com/b/vsproject/archive/2009/07/07/vc-directories.aspx)[Propiedades y hojas de propiedades heredadas](http://blogs.msdn.com/b/vsproject/archive/2009/06/23/inherited-properties-and-property-sheets.aspx) y [Guía de actualización de proyectos de C\+\+ de Visual Studio 2010](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx).  
  
## Tipos de directorio  
 También puede especificar otros directorios, de la manera siguiente.  
  
 **Directorios de archivos ejecutables**  
 Directorios donde buscar archivos ejecutables.  Corresponde a la variable de entorno **PATH**.  
  
 **Directorios de archivos de inclusión**  
 Directorios donde buscar archivos de inclusión a los que se hace referencia en el código fuente.  Corresponde a la variable de entorno **INCLUDE**.  
  
 **Directorios de referencia**  
 Directorios donde buscar archivos de ensamblado y módulo \(metadatos\) a los que la directiva [\#using](../preprocessor/hash-using-directive-cpp.md) hace referencia en el código fuente.  Corresponde a la variable de entorno **LIBPATH**.  
  
 **Directorios de archivos de bibliotecas**  
 Directorios donde buscar archivos de bibliotecas \(.lib\); esto incluye las bibliotecas en tiempo de ejecución.  Corresponde a la variable de entorno **LIB**.  Este valor no se aplica a los archivos .obj; para crear vínculos a un archivo .obj, en la página de propiedades **General** del [Vinculador](../ide/linker-property-pages.md), seleccione **Dependencias de biblioteca adicionales** y especifique la ruta de acceso relativa del archivo.  
  
 **Directorios de archivos de códigos fuente**  
 Directorios donde buscar archivos de código fuente para utilizar con IntelliSense.  
  
 **Excluir directorios**  
 Directorios en los que no se va a buscar cuando se comprueban las dependencias de compilación.  
  
#### Para especificar o modificar valores de directorio  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del proyecto que desea cambiar y, a continuación, elija **Propiedades**.  
  
2.  En el panel izquierdo del cuadro de diálogo **Páginas de propiedades**, expanda **Propiedades de configuración** y, a continuación, seleccione **Directorios de VC\+\+**.  
  
3.  Para modificar una de las listas de directorios, selecciónela, elija el botón de flecha abajo situado a la derecha y, a continuación, elija **Editar**.  
  
     En el cuadro del cuadro de diálogo que aparece, puede agregar o quitar valores, y puede reorganizar el orden en que aparecen los valores.  También puede cambiar si el proyecto hereda alguna configuración activando o desactivando **Heredar de primario o valores pred. del proyecto**.  
  
## Compartir la configuración  
 Puede compartir propiedades del proyecto con otros usuarios o en varios equipos.  Para obtener más información, vea [Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).  
  
## Vea también  
 [Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md)