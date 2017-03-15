---
title: "/LINENUMBERS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/linenumbers"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/LINENUMBERS (opción de dumpbin)"
  - "números de línea"
  - "LINENUMBERS (opción de dumpbin)"
  - "-LINENUMBERS (opción de dumpbin)"
ms.assetid: 1681d582-2c2f-484e-9920-109959549055
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /LINENUMBERS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/LINENUMBERS  
```  
  
## Comentarios  
 Esta opción muestra los números de línea COFF.  En un archivo objeto existirán números de línea si se compiló con las opciones Base de datos de programa \(\/Zi\), Compatible con C7 \(\/Z7\) o Sólo números de línea \(\/Zd\).  Un archivo ejecutable o una DLL contendrá números de línea COFF si se vinculó con la opción Generar información de depuración \(\/DEBUG\).  
  
 En los archivos producidos con la opción de compilador [\/GL](../../build/reference/gl-whole-program-optimization.md) sólo está disponible la opción [\/HEADERS](../../build/reference/headers.md) de DUMPBIN.  
  
## Vea también  
 [Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)