---
title: "/IMPORTS (DUMPBIN) | Microsoft Docs"
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
  - "/imports"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/IMPORTS (opción de dumpbin)"
  - "IMPORTS (opción de dumpbin)"
  - "-IMPORTS (opción de dumpbin)"
ms.assetid: 6a296216-2b1b-40f8-8736-cd4553a22456
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /IMPORTS (DUMPBIN)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/IMPORTS[:file]  
```  
  
 Esta opción muestra la lista de archivos DLL \(tanto los vinculados estáticamente como los de [carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)\) que se importan en un archivo ejecutable o un archivo DLL, y todas las importaciones individuales realizadas desde cada una de estas DLL.  
  
 El argumento `file` opcional permite especificar que sólo se muestren las importaciones de esa DLL.  Por ejemplo:  
  
```  
dumpbin /IMPORTS:msvcrt.dll  
```  
  
## Comentarios  
 Los resultados mostrados por esta opción son similares a los producidos por la opción [\/EXPORTS](../../build/reference/dash-exports.md).  
  
 En los archivos producidos con la opción de compilador [\/GL](../../build/reference/gl-whole-program-optimization.md) sólo está disponible la opción [\/HEADERS](../../build/reference/headers.md) de DUMPBIN.  
  
## Vea también  
 [Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)