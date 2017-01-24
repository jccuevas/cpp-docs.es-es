---
title: "/INCLUDE (Forzar referencias de s&#237;mbolos) | Microsoft Docs"
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
  - "/include"
  - "VC.Project.VCLinkerTool.ForceSymbolReferences"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/INCLUDE (opción del vinculador)"
  - "forzar referencias de símbolos (opción del vinculador)"
  - "INCLUDE (opción del vinculador)"
  - "-INCLUDE (opción del vinculador)"
  - "forzar referencias de símbolos (vinculador)"
  - "símbolos, agregar a tabla de símbolos"
ms.assetid: 4a039677-360a-480f-bd0b-448e239b449c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /INCLUDE (Forzar referencias de s&#237;mbolos)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/INCLUDE:symbol  
```  
  
## Comentarios  
 donde:  
  
 `symbol`  
 Especifica un símbolo que se ha de agregar a la tabla de símbolos.  
  
## Comentarios  
 La opción \/INCLUDE indica al vinculador que agregue un símbolo especificado a la tabla de símbolos.  
  
 Para especificar varios símbolos, escriba una coma \(,\), un punto y coma \(;\) o un espacio entre sus nombres.  En la línea de comandos, especifique \/INCLUDE:`symbol` una vez para cada símbolo.  
  
 Para resolver `symbol`, el vinculador agregará al programa el objeto que contenga la definición de cada símbolo.  Esta característica resulta útil para incluir un objeto de biblioteca que, de otra manera, no se vincularía con el programa.  
  
 La especificación de un símbolo con esta opción reemplaza la eliminación del símbolo mediante [\/OPT:REF](../../build/reference/opt-optimizations.md).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Entrada**.  
  
4.  Modifique la propiedad **Forzar referencias de símbolos**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ForceSymbolReferences%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)