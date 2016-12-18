---
title: "/TLBOUT (Dar nombre a un archivo .TLB) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.TypeLibraryFile"
  - "/tlbout"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".tlb (archivos), cambiar nombre"
  - "/TLBOUT (opción del vinculador)"
  - "tlb (archivos), cambiar nombre"
  - "TLBOUT (opción del vinculador)"
  - "-TLBOUT (opción del vinculador)"
ms.assetid: 0df6d078-2e48-46c9-a1a5-02674d85dce8
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /TLBOUT (Dar nombre a un archivo .TLB)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/TLBOUT:[path\]filename  
```  
  
## Comentarios  
 donde:  
  
 *ruta de acceso*  
 Especificación de la ruta de acceso absoluta o relativa donde debe crearse el archivo .tlb.  
  
 *filename*  
 Especifica el nombre del archivo .tlb creado por el compilador MIDL.  No se presupone una extensión de archivo; si se desea la extensión .tlb, deberá especificarse *filename*.tlb.  
  
## Comentarios  
 La opción \/TLBOUT especifica el nombre y la extensión del archivo .tlb.  
  
 El vinculador de Visual C\+\+ llama al compilador MIDL al vincular proyectos que tienen el atributo [module](../../windows/module-cpp.md).  
  
 Si no se especifica la opción \/TLBOUT, el archivo .tlb obtendrá el nombre a partir de la opción [\/IDLOUT](../../build/reference/idlout-name-midl-output-files.md) *filename*.  Si no se especifica \/IDLOUT, el archivo .tlb recibirá el nombre vc70.tlb.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **IDL incrustado**.  
  
4.  Modifique la propiedad **Biblioteca de tipos**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)   
 [\/IGNOREIDL \(No procesar atributos en MIDL\)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [\/MIDL \(Especificar las opciones de la línea de comandos de MIDL\)](../../build/reference/midl-specify-midl-command-line-options.md)   
 [Building an Attributed Program](../../windows/building-an-attributed-program.md)