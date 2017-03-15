---
title: "/LARGEADDRESSAWARE (Procesar direcciones largas) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.LargeAddressAware"
  - "/largeaddressaware"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/LARGEADDRESSAWARE (opción del vinculador)"
  - "LARGEADDRESSAWARE (opción del vinculador)"
  - "-LARGEADDRESSAWARE (opción del vinculador)"
ms.assetid: a29756c8-e893-47a9-9750-1f0d25359385
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /LARGEADDRESSAWARE (Procesar direcciones largas)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/LARGEADDRESSAWARE[:NO]  
```  
  
## Comentarios  
 La opción \/LARGEADDRESSAWARE indica al vinculador que la aplicación puede controlar direcciones superiores a 2 gigabytes.  En los compiladores de 64 bits, esta opción está habilitada de forma predeterminada.  En los compiladores de 32 bits, \/LARGEADDRESSAWARE:NO está habilitado si \/LARGEADDRESSAWARE no se especifica de otra forma en la línea del vinculador.  
  
 Si se vincula una aplicación por medio de \/LARGEADDRESSAWARE, DUMPBIN [\/HEADERS](../../build/reference/headers.md) mostrará la información pertinente.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Sistema**.  
  
4.  Modifique la propiedad **Habilitar direcciones largas**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)