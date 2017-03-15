---
title: "/PGD (Especificar la base de datos para las optimizaciones guiadas por perfiles) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.ProfileGuidedDatabase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/PGD (opción del vinculador)"
  - "-PGD (opción del vinculador)"
ms.assetid: 9f312498-493b-461f-886f-92652257e443
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /PGD (Especificar la base de datos para las optimizaciones guiadas por perfiles)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\/PGD:`filename`  
  
## Comentarios  
 donde:  
  
 `filename`  
 Especifica el nombre del archivo .pgd que se utilizará para guardar información sobre el programa en ejecución.  
  
## Comentarios  
 Cuando utilice [\/LTCG:PGINSTRUMENT](../../build/reference/ltcg-link-time-code-generation.md), use \/PGD para especificar un nombre o ubicación no predeterminados para el archivo .pgd.  Si no especifica \/PGD, el nombre del archivo .pgd será el mismo que el del archivo de salida \(.exe o .dll\) y se creará en el mismo directorio desde el que se invocó el vínculo.  
  
 Cuando utilice \/LTCG:PGOPTIMIZE, use \/PGD para especificar el nombre del archivo .pgd que se utilizará para crear la imagen optimizada.  
  
 Para obtener más información, vea [Optimización guiada por perfiles \(PGO\)](../../build/reference/profile-guided-optimizations.md).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el nodo **Vinculador**.  
  
4.  Seleccione la página de propiedades **Optimización**.  
  
5.  Modifique la propiedad **Base de datos guiada por perfiles**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)