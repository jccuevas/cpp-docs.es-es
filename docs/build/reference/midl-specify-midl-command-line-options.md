---
title: "/MIDL (Especificar las opciones de la l&#237;nea de comandos de MIDL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/midl"
  - "VC.Project.VCLinkerTool.MidlCommandFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MIDL (opción del vinculador)"
  - "MIDL"
  - "MIDL (opción del vinculador)"
  - "-MIDL (opción del vinculador)"
  - "MIDL, opciones de la línea de comandos"
ms.assetid: 22dc259e-b34c-4ed3-a380-4beb734482c1
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /MIDL (Especificar las opciones de la l&#237;nea de comandos de MIDL)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MIDL:@file  
```  
  
## Comentarios  
 donde:  
  
 `file`  
 Nombre del archivo que contiene las [opciones de la línea de comandos de MIDL](http://msdn.microsoft.com/library/windows/desktop/aa366839).  
  
## Comentarios  
 Todas las opciones para la conversión de un archivo IDL en archivo TLB deberán indicarse en `file`; las opciones de la línea de comandos de MIDL no podrán especificarse en la línea de comandos del vinculador.  Si no se especifica \/MIDL, se invocará el compilador MIDL únicamente con el nombre del archivo IDL, sin otras opciones.  
  
 El archivo deberá contener una sola opción de la línea de comandos de MIDL por línea.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **IDL incrustado**.  
  
4.  Modifique la propiedad Co**mandos de MIDL**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)   
 [\/IDLOUT \(Dar nombre a los archivos de resultados de MIDL\)](../../build/reference/idlout-name-midl-output-files.md)   
 [\/IGNOREIDL \(No procesar atributos en MIDL\)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [\/TLBOUT \(Dar nombre a un archivo .TLB\)](../../build/reference/tlbout-name-dot-tlb-file.md)   
 [Building an Attributed Program](../../windows/building-an-attributed-program.md)