---
title: "_CIpow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CIpow"
apilocation: 
  - "msvcr100.dll"
  - "msvcr110.dll"
  - "msvcr120.dll"
  - "msvcr80.dll"
  - "msvcr110_clr0400.dll"
  - "msvcrt.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "CIpow"
  - "_CIpow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CIpow intrínseco"
  - "_CIpow intrínseco"
ms.assetid: 477aaf0c-ac58-4252-89dd-9f3e35d47536
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# _CIpow
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Calcula *x* provocado elevado a *y* según los valores superiores de la pila.  
  
## Sintaxis  
  
```  
void __cdecl _CIpow();  
```  
  
## Comentarios  
 Esta versión de la función de `pow` tiene una convención de llamada especializada que el compilador entienda.  Acelera la ejecución porque evita que las copias genera y contribuye a la asignación del registro.  
  
 El valor resultante se incrusta en la parte superior de la pila.  
  
## Requisitos  
 **Plataforma:** x86  
  
## Vea también  
 [Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [pow, powf, powl](../c-runtime-library/reference/pow-powf-powl.md)