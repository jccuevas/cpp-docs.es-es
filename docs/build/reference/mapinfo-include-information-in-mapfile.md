---
title: "/MAPINFO (Incluir informaci&#243;n en el archivo de asignaciones) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.MapLines"
  - "VC.Project.VCLinkerTool.MapInfoFixups"
  - "VC.Project.VCLinkerTool.MapExports"
  - "/mapinfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MAPINFO (opción del vinculador)"
  - "MAPINFO (opción del vinculador)"
  - "-MAPINFO (opción del vinculador)"
ms.assetid: 533d2bce-f9b7-4fea-ae1c-0b4864c9d10b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /MAPINFO (Incluir informaci&#243;n en el archivo de asignaciones)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MAPINFO:EXPORTS  
```  
  
## Comentarios  
 La opción \/MAPINFO le indica al vinculador que debe incluir la información especificada en un archivo de asignaciones, que se crea especificando la opción [\/MAP](../../build/reference/map-generate-mapfile.md).  EXPORTS indica al vinculador que incluya las funciones exportadas.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Depurar**.  
  
4.  Modifique las propiedades de **Exportaciones de asignaciones**:  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapExports%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)