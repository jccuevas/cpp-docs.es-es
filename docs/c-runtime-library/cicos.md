---
title: "_CIcos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CIcos"
apilocation: 
  - "msvcr90.dll"
  - "msvcrt.dll"
  - "msvcr120.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
apitype: "DLLExport"
f1_keywords: 
  - "CIcos"
  - "_CIcos"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CIcos intrínseco"
  - "CIcos intrínseco"
ms.assetid: 6fc203fb-66f3-4ead-9784-f85833c26f1b
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# _CIcos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Calcula el coseno del valor superior de la pila.  
  
## Sintaxis  
  
```  
void __cdecl _CIcos();  
```  
  
## Comentarios  
 Esta versión de la función de `cos` tiene una convención de llamada especializada que el compilador entienda.  Acelera la ejecución porque evita que las copias genera y contribuye a la asignación del registro.  
  
 El valor resultante se incrusta en la parte superior de la pila.  
  
## Requisitos  
 **Plataforma:** x86  
  
## Vea también  
 [Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [cos, cosf, cosl, cosh, coshf, coshl](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)