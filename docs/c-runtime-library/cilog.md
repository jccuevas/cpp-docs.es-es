---
title: "_CIlog | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CIlog"
apilocation: 
  - "msvcr90.dll"
  - "msvcr120.dll"
  - "msvcr80.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
  - "msvcrt.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_CIlog"
  - "CIlog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CIlog intrínseco"
  - "CIlog intrínseco"
ms.assetid: 23503854-ddaa-4fe0-a4a3-7fbb3a43bdec
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# _CIlog
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Calcula el logaritmo natural del valor superior de la pila.  
  
## Sintaxis  
  
```  
void __cdecl _CIlog();  
```  
  
## Comentarios  
 Esta versión de la función de `log` tiene una convención de llamada especializada que el compilador entienda.  Acelera la ejecución porque evita que las copias genera y contribuye a la asignación del registro.  
  
 El valor resultante se incrusta en la parte superior de la pila.  
  
## Requisitos  
 **Plataforma:** x86  
  
## Vea también  
 [Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [log, logf, log10, log10f](../c-runtime-library/reference/log-logf-log10-log10f.md)