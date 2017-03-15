---
title: "_CIatan2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CIatan2"
apilocation: 
  - "msvcr80.dll"
  - "msvcrt.dll"
  - "msvcr120.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr100.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "CIatan2"
  - "_CIatan2"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CIatan2 intrínseco"
  - "CIatan2 intrínseco"
ms.assetid: 31f8cc78-b79f-4576-b73b-8add18e08680
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# _CIatan2
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Calcula el arco tangente de *x* \/ *y* donde valores *x* y *y* en la parte superior de la pila.  
  
## Sintaxis  
  
```  
void __cdecl _CIatan2();  
```  
  
## Comentarios  
 Esta versión de la función de `atan2` tiene una convención de llamada especializada que el compilador entienda.  Acelera la ejecución porque evita que las copias genera y contribuye a la asignación del registro.  
  
 El valor resultante se incrusta en la parte superior de la pila.  
  
## Requisitos  
 **Plataforma:** x86  
  
## Vea también  
 [Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [atan, atanf, atanl, atan2, atan2f, atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)