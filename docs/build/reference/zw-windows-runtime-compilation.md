---
title: "/ZW (Compilaci&#243;n de Windows en tiempo de ejecuci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.CompileAsWinRT"
  - "/zw"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ZW"
  - "/ZW (opción del compilador)"
  - "Windows en tiempo de ejecución (opción del compilador)"
  - "-ZW"
  - "-ZW (opción del compilador)"
ms.assetid: 0fe362b0-9526-498b-96e0-00d7a965a248
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ZW (Compilaci&#243;n de Windows en tiempo de ejecuci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Compila el código fuente para admitir [!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] \([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]\) y poder crear aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  
  
 Cuando use **\/ZW** para compilar, especifique siempre **\/EHsc**.  
  
## Sintaxis  
  
```cpp  
/ZW /EHsc /ZW:nostdlib /EHsc  
```  
  
## Argumentos  
 nostdlib  
 Indica que Platform.winmd, Windows.Foundation.winmd y otros archivos de metadatos de Windows \(.winmd\) predeterminados no se incluyen automáticamente en la compilación,  sino que se debe usar la opción del compilador [\/FU \(Archivo de \#using de nombre forzado\)](../../build/reference/fu-name-forced-hash-using-file.md) para especificar explícitamente los archivos de metadatos de Windows.  
  
## Comentarios  
 Cuando especifica la opción **\/ZW**, el compilador admite estas características:  
  
-   Los archivos de metadatos necesarios, los espacios de nombres, los tipos de datos y las funciones que requiere la aplicación para ejecutarse en el [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
-   El recuento de referencias automático de objetos de [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] y el descarte automático de un objeto cuando su recuento de referencias llega a cero.  
  
 Dado que el enlazador incremental no admite los metadatos de Windows incluidos en los archivos .obj con la opción **\/ZW**, la opción [\/Gm \(Habilitar recompilación mínima\)](../../build/reference/gm-enable-minimal-rebuild.md) es incompatible con **\/ZW**.  
  
 Para obtener más información, vea [Referencia del lenguaje Visual C\+\+](../Topic/Visual%20C++%20Language%20Reference%20\(C++-CX\).md).  
  
## Requisitos  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)