---
title: "/MACHINE (Especificar la plataforma de destino) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.TargetMachine"
  - "/machine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MACHINE (opción del vinculador)"
  - "MACHINE (opción del vinculador)"
  - "-MACHINE (opción del vinculador)"
  - "archivos de asignaciones, crear vinculador"
  - "plataforma de destino"
ms.assetid: 8d41bf4b-7e53-4ab9-9085-d852b08d31c2
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /MACHINE (Especificar la plataforma de destino)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MACHINE:{ARM|EBC|X64|X86}  
```  
  
## Comentarios  
 La opción \/MACHINE especifica la plataforma de destino para el programa.  
  
 Normalmente, no tiene que especificar la opción \/MACHINE.  LINK infiere el tipo de equipo a partir de los archivos .obj.  Sin embargo, en determinados casos, LINK no puede determinar el tipo de equipo y genera un [error de las herramientas del vinculador LNK1113](../../error-messages/tool-errors/linker-tools-error-lnk1113.md).  Si se produce un error de este tipo, especifique \/MACHINE.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Avanzadas**.  
  
4.  Modifique la propiedad **Equipo de destino**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TargetMachine%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)