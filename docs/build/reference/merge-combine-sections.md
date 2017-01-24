---
title: "/MERGE (Combinar secciones) | Microsoft Docs"
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
  - "/merge"
  - "VC.Project.VCLinkerTool.MergeSections"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MERGE (opción del vinculador)"
  - "MERGE (opción del vinculador)"
  - "-MERGE (opción del vinculador)"
  - "secciones"
  - "secciones, combinar"
  - "secciones, asignar nombre"
ms.assetid: 10fb20c2-0b3f-4c8d-98a8-f69aedf03d52
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /MERGE (Combinar secciones)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MERGE:from=to  
```  
  
## Comentarios  
 La opción \/MERGE combina la primera sección \(*from*\) con la segunda \(*to*\), y le asigna a la sección resultante el nombre de *to*.  Por ejemplo, `/merge:.rdata=.text`.  
  
 Si la segunda sección no existe, LINK sustituirá el nombre de la sección *from* por *to*.  
  
 Esta opción puede ser útil para crear controladores VxD y reemplazar los nombres de sección generados por el compilador.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Avanzadas**.  
  
4.  Modifique la propiedad **Combinar secciones**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergeSections%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)