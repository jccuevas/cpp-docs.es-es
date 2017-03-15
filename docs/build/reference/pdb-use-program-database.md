---
title: "/PDB (Utilizar la base de datos de programa) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/pdb"
  - "VC.Project.VCLinkerTool.ProgramDatabaseFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pdb (archivos), crear"
  - "/PDB (opción del vinculador)"
  - "PDB (archivos), crear"
  - "PDB (opción del vinculador)"
  - "-PDB (opción del vinculador)"
ms.assetid: d23db0ce-10cb-427a-bc60-d6b2a852723d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /PDB (Utilizar la base de datos de programa)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/PDB:filename  
```  
  
## Comentarios  
 donde:  
  
 *filename*  
 Nombre especificado por el usuario para la base de datos de programa \(PDB\) que crea el vinculador.  Reemplaza al nombre predeterminado.  
  
## Comentarios  
 De forma predeterminada, si se especifica [\/DEBUG](../../build/reference/debug-generate-debug-info.md), el vinculador creará una base de datos de programa \(PDB\) con información de depuración.  El nombre de archivo predeterminado de dicha base de datos incluye el nombre base del programa con la extensión .pdb.  
  
 Con \/PDB:*filename* se podrá especificar el nombre del archivo PDB.  Si no se especifica \/DEBUG, la opción \/PDB se pasará por alto.  
  
 Los archivos PDB pueden ser de hasta 2 GB.  
  
 Para obtener más información, vea [Archivos .pdb como entrada del vinculador](../../build/reference/dot-pdb-files-as-linker-input.md).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Depurar**.  
  
4.  Modifique la propiedad **Generar archivo de base de datos de programas**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProgramDatabaseFile%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)