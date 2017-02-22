---
title: "/IDLOUT (Dar nombre a los archivos de resultados de MIDL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/idlout"
  - "VC.Project.VCLinkerTool.MergedIDLBaseFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".idl (archivos), ruta de acceso"
  - "/IDLOUT (opción del vinculador)"
  - "IDL (archivos), ruta de acceso"
  - "IDLOUT (opción del vinculador)"
  - "-IDLOUT (opción del vinculador)"
  - "MIDL"
  - "MIDL, nombres de archivos de resultados"
ms.assetid: 10d00a6a-85b4-4de1-8732-e422c6931509
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /IDLOUT (Dar nombre a los archivos de resultados de MIDL)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/IDLOUT:[path\]filename  
```  
  
## Parámetros  
 *ruta de acceso*  
 Especificación de una ruta de acceso absoluta o relativa.  El especificar una ruta sólo afecta a la ubicación de los archivos .idl; los demás archivos se sitúan en el directorio del proyecto.  
  
 *filename*  
 Especifica el nombre del archivo .idl creado por el compilador MIDL.  No se presupone una extensión de archivo, por lo que, si se desea una extensión .idl, deberá especificarse *filename*.idl.  
  
## Comentarios  
 La opción \/IDLOUT especifica el nombre y la extensión del archivo .idl.  
  
 El vinculador de Visual C\+\+ llama al compilador MIDL al vincular proyectos que tienen el atributo [module](../../windows/module-cpp.md).  
  
 \/IDLOUT también especifica los nombres de otros archivos de salida asociados al compilador MIDL:  
  
-   *filename*.tlb  
  
-   *filename*\_p.c  
  
-   *filename*\_i.c  
  
-   *filename*.h  
  
 *filename* es el parámetro que se pasa a \/IDLOUT.  Si no se especifica [\/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md), el archivo .tlb obtendrá su nombre de \/TLBOUT *filename*.  
  
 Si no se especifica ni \/IDLOUT ni \/TLBOUT, el vinculador creará vc70.tlb, vc70.idl, vc70\_p.c, vc70\_i.c y vc70.h.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **IDL incrustado**.  
  
4.  Modifique la propiedad **Combinar nombre de archivo de base IDL**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)   
 [\/IGNOREIDL \(No procesar atributos en MIDL\)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)   
 [\/MIDL \(Especificar las opciones de la línea de comandos de MIDL\)](../../build/reference/midl-specify-midl-command-line-options.md)   
 [Building an Attributed Program](../../windows/building-an-attributed-program.md)