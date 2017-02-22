---
title: "_CIfmod | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CIfmod"
apilocation: 
  - "msvcrt.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
  - "msvcr110.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_CIfmod"
  - "CIfmod"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CIfmod intrínseco"
  - "_CIfmod intrínseco"
ms.assetid: 7c050653-7ec6-4810-b3a7-7a0057ea65ed
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# _CIfmod
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Calcula el resto flotante de los dos valores superiores de la pila.  
  
## Sintaxis  
  
```  
void __cdecl _CIfmod();  
```  
  
## Comentarios  
 Esta versión de la función de `fmod` tiene una convención de llamada especializada que el compilador entienda.  Acelera la ejecución porque evita que las copias genera y contribuye a la asignación del registro.  
  
 El valor resultante se incrusta en la parte superior de la pila.  
  
## Requisitos  
 **Plataforma:** x86  
  
## Vea también  
 [Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fmod, fmodf](../c-runtime-library/reference/fmod-fmodf.md)