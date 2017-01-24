---
title: "/MAP (Generar archivo de asignaciones) | Microsoft Docs"
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
  - "/map"
  - "VC.Project.VCLinkerTool.MapFileName"
  - "VC.Project.VCLinkerTool.GenerateMapFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MAP (opción del vinculador)"
  - "generar archivo de asignaciones (opción del vinculador)"
  - "MAP (opción del vinculador)"
  - "-MAP (opción del vinculador)"
  - "mapfile (opción del vinculador)"
  - "archivos de asignaciones, crear vinculador"
  - "archivos de asignaciones, información sobre el programa que se vincula"
  - "archivos de asignaciones, especificar nombre de archivo"
ms.assetid: 9ccce53d-4e36-43da-87b0-7603ddfdea63
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /MAP (Generar archivo de asignaciones)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MAP[:filename]  
```  
  
## Comentarios  
 donde:  
  
 *filename*  
 Nombre del archivo de asignaciones especificado por el usuario.  Reemplaza al nombre predeterminado.  
  
## Comentarios  
 La opción \/MAP indica al vinculador que cree un archivo de asignaciones.  
  
 De forma predeterminada, el vinculador le asignará al archivo de asignaciones el nombre base del programa y la extensión .map.  *filename*, de carácter opcional, permite reemplazar el nombre predeterminado de un archivo de asignaciones.  
  
 Un archivo de asignaciones es un archivo de texto que contiene la siguiente información sobre el programa que se está vinculando:  
  
-   El nombre del módulo, que coincide con el nombre base del archivo  
  
-   La marca de tiempo del encabezado del archivo de programa \(no del sistema de archivos\)  
  
-   Una lista de grupos del programa, con sus correspondientes direcciones de inicio \(con el formato *sección*:*desplazamiento*\), longitudes, nombres de grupo y clases  
  
-   Una lista de símbolos públicos, junto con cada dirección \(con el formato *sección*:*desplazamiento*\), nombre de símbolo, dirección plana y archivo .obj donde esté definido el símbolo  
  
-   El punto de entrada \(con el formato *sección*:*desplazamiento*\)  
  
 La opción [\/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md) especifica la información adicional que debe incluirse en el archivo de asignaciones.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Depurar**.  
  
4.  Modifique la propiedad **Generar archivo de asignaciones**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateMapFile%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapFileName%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)