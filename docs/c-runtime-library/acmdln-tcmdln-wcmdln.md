---
title: "_acmdln, _tcmdln, _wcmdln | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wcmdln"
  - "_acmdln"
apilocation: 
  - "msvcrt.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_acmdln"
  - "acmdln"
  - "_wcmdln"
  - "wcmdln"
  - "_tcmdln"
  - "tcmdln"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_acmdln (variable global)"
  - "_tcmdln (variable global)"
  - "_wcmdln (variable global)"
  - "acmdln (variable global)"
  - "tcmdln (variable global)"
  - "wcmdln (variable global)"
ms.assetid: 4fc0a6a0-3f93-420a-a19f-5276061ba539
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# _acmdln, _tcmdln, _wcmdln
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Variable global CRT interna.  Línea de comandos.  
  
## Sintaxis  
  
```  
char * _acmdln; wchar_t * _wcmdln;  #ifdef WPRFLAG    #define _tcmdln _wcmdln #else    #define _tcmdln _acmdln  
```  
  
## Comentarios  
 Estas variables de CRT internas almacenan la línea de comandos completa.  Se muestran en los símbolos exportados de CRT, pero usarlas en su código no está previsto.  `_acmdln` almacena los datos como una cadena de caracteres.  `_wcmdln` almacena los datos como una cadena de caracteres anchos.  `_tcmdln` se puede definir como `_acmdln` o  `_wcmdln`, según lo que sea apropiado.  
  
## Vea también  
 [Variables globales](../c-runtime-library/global-variables.md)