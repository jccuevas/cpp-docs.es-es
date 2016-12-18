---
title: "/IGNOREIDL (No procesar atributos en MIDL) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.IgnoreEmbeddedIDL"
  - "/ignoreidl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/IGNOREIDL (opción del vinculador)"
  - "IGNOREIDL (opción del vinculador)"
  - "-IGNOREIDL (opción del vinculador)"
ms.assetid: 29514098-6a1c-4317-af2f-1dc268972780
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /IGNOREIDL (No procesar atributos en MIDL)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/IGNOREIDL  
```  
  
## Comentarios  
 La opción \/IGNOREIDL especifica que los [atributos IDL](../../windows/idl-attributes.md) del código fuente no deben procesarse en archivos .idl.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **IDL incrustado**.  
  
4.  Modifique la propiedad **Omitir IDL incrustado**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreEmbeddedIDL%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)   
 [\/IDLOUT \(Dar nombre a los archivos de resultados de MIDL\)](../../build/reference/idlout-name-midl-output-files.md)   
 [\/TLBOUT \(Dar nombre a un archivo .TLB\)](../../build/reference/tlbout-name-dot-tlb-file.md)   
 [\/MIDL \(Especificar las opciones de la línea de comandos de MIDL\)](../../build/reference/midl-specify-midl-command-line-options.md)   
 [Building an Attributed Program](../../windows/building-an-attributed-program.md)