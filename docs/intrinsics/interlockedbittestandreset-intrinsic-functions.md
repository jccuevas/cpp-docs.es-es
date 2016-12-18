---
title: "Funciones intr&#237;nsecas _interlockedbittestandreset | Microsoft Docs"
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
  - "_interlockedbittestandreset_rel"
  - "_interlockedbittestandreset64"
  - "_interlockedbittestandreset64_HLERelease"
  - "_interlockedbittestandreset_HLERelease"
  - "_interlockedbittestandreset_HLEAcquire"
  - "_interlockedbittestandreset_acq"
  - "_interlockedbittestandreset_cpp"
  - "_interlockedbittestandreset_nf"
  - "_interlockedbittestandreset64_cpp"
  - "_interlockedbittestandreset64_HLEAcquire"
  - "_interlockedbittestandreset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Intrínseco _interlockedbittestandreset"
  - "Intrínseco _interlockedbittestandreset64"
  - "Instrucción lock_btr"
ms.assetid: 9bbb1442-f2e9-4dc2-b0da-97f3de3493b9
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Funciones intr&#237;nsecas _interlockedbittestandreset
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera una instrucción que establece el bit `b` de la dirección `a` en cero y devuelve su valor original.  
  
## Sintaxis  
  
```  
unsigned char _interlockedbittestandreset(    long *a,    long b ); unsigned char _interlockedbittestandreset_acq(    long *a,    long b ); unsigned char _interlockedbittestandreset_HLEAcquire(    long *a,    long b ); unsigned char _interlockedbittestandreset_HLERelease(    long *a,    long b ); unsigned char _interlockedbittestandreset_nf(    long *a,    long b ); unsigned char _interlockedbittestandreset_rel(    long *a,    long b );  unsigned char _interlockedbittestandreset64(    __int64 *a,    __int64 b );  unsigned char _interlockedbittestandreset64_HLEAcquire(    __int64 *a,    __int64 b ); unsigned char _interlockedbittestandreset64_HLERelease(    __int64 *a,    __int64 b );  
```  
  
#### Parámetros  
 \[in\] `a`  
 Puntero a la memoria que se va a examinar.  
  
 \[in\] `b`  
 La posición de bit que se va a para probar.  
  
## Valor devuelto  
 El valor original del bit en la posición especificada por `b`.  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|Header|  
|------------------------|------------------|------------|  
|`_interlockedbittestandreset`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_interlockedbittestandreset_acq`, `_interlockedbittestandreset_nf`, `_interlockedbittestandreset_rel`|ARM|\<intrin.h\>|  
|`_interlockedbittestandreset_HLEAcquire`, `_interlockedbittestandreset_HLERelease`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h\>|  
|`_interlockedbittestandreset64`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_interlockedbittestandreset64_HLEAcquire`, `_interlockedbittestandreset64_HLERelease`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h\>|  
  
## Comentarios  
 En x86 y procesadores [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)], estos intrínsecos usan la instrucción `lock btr`, que lee y establece el bit especificado en cero en una operación atómica.  
  
 En procesadores ARM, utilice los intrínsecos con sufijos `_acq` y `_rel` para adquirir y liberar semántica, como al principio y al final de una sección crítica.  Los intrínsecos ARM con un sufijo `_nf` \("sin límite"\) no actúan como una barrera de memoria.  
  
 En las plataformas de Intel que admiten instrucciones de Elisión de bloqueo de Hardware \(HLE\), los intrínsecos con sufijos `_HLEAcquire` y `_HLERelease` incluyen una sugerencia para el procesador que puede acelerar el rendimiento mediante la eliminación de un paso de escritura de bloqueo en el hardware.  Si se llama a estos intrínsecos en procesadores que no son compatibles con HLE, se omite la sugerencia.  
  
 Estas rutinas solo están disponibles como intrínsecos.  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [Conflictos con el compilador de x86](../build/conflicts-with-the-x86-compiler.md)