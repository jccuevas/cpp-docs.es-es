---
title: "_InterlockedAddLargeStatistic | Microsoft Docs"
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
  - "_InterlockedAddLargeStatistic"
  - "_InterlockedAddLargeStatistic_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_InterlockedAddLargeStatistic (función intrínseca)"
  - "InterlockedAddLargeStatistic (función intrínseca)"
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _InterlockedAddLargeStatistic
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Realiza una suma de bloqueo en la que el primer operando es un valor de 64 bits.  
  
## Sintaxis  
  
```  
long _InterlockedAddLargeStatistic(  
   __int64 volatile * Addend,  
   long Value  
);  
```  
  
#### Parámetros  
 \[in, out\] `Addend`  
 Un puntero al primer operando a la operación add.  El valor indicado a es sustituido por el resultado de la suma.  
  
 \[in\] `Value`  
 El segundo operando; valor que se va a agregar al primer operando.  
  
## Valor devuelto  
 El valor del segundo operando.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`_InterlockedAddLargeStatistic`|x86|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Este intrínseco no es atómico porque se implementa como dos instrucciones bloqueadas independientes.  Una lectura 64 bits atómica que aparece en otro subproceso durante la ejecución de este intrínseco podría producir un valor incoherente leídos.  
  
 Esta función se comporta como barrera de lectura y escritura.  Para obtener más información, vea [más \_ReadWriteBarrier](../intrinsics/readwritebarrier.md).  
  
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [Conflictos con el compilador de x86](../build/conflicts-with-the-x86-compiler.md)