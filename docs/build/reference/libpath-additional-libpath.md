---
title: "/LIBPATH (Directorios de bibliotecas adicionales) | Microsoft Docs"
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
  - "/libpath"
  - "VC.Project.VCLinkerTool.AdditionalLibraryDirectories"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/LIBPATH (opción del vinculador)"
  - "ruta de acceso a la biblioteca adicional (opción del vinculador)"
  - "reemplazo de ruta de acceso a la biblioteca de entorno"
  - "LIBPATH (opción del vinculador)"
  - "-LIBPATH (opción del vinculador)"
  - "ruta de acceso a la biblioteca (opción del vinculador)"
ms.assetid: 7240af0b-9a3d-4d53-8169-2a92cd6958ba
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /LIBPATH (Directorios de bibliotecas adicionales)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/LIBPATH:dir  
```  
  
## Comentarios  
 donde:  
  
 `dir`  
 Especifica una ruta de acceso en la que buscará el vinculador antes de hacerlo en la ruta especificada en la opción de entorno LIB.  
  
## Comentarios  
 Esta opción se utiliza para reemplazar la ruta de acceso de la biblioteca de entorno.  El vinculador busca en primer lugar en la ruta de acceso especificada por esta opción, y, a continuación, en la ruta especificada en la variable de entorno LIB.  Sólo se puede especificar un directorio por cada opción \/LIBPATH que se especifique.  Para especificar más de un directorio, será necesario utilizar varias opciones \/LIBPATH.  El vinculador buscará por orden en los directorios especificados.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **General**.  
  
4.  Modifique la propiedad **Directorios de bibliotecas adicionales**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalLibraryDirectories%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)