---
title: "Funciones intr&#237;nsecas _interlockedbittestandset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_interlockedbittestandset_cpp"
  - "_interlockedbittestandset_HLEAcquire"
  - "_interlockedbittestandset64"
  - "_interlockedbittestandset"
  - "_interlockedbittestandset_rel"
  - "_interlockedbittestandset64_HLEAcquire"
  - "_interlockedbittestandset_HLERelease"
  - "_interlockedbittestandset_acq"
  - "_interlockedbittestandset_nf"
  - "_interlockedbittestandset64_cpp"
  - "_interlockedbittestandset64_HLERelease"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Intrínseco _interlockedbittestandset"
  - "Intrínseco _interlockedbittestandset64"
  - "Instrucción lock_bts"
ms.assetid: b1b7e334-53ea-48cf-ba60-5fa3ef51a1fc
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# Funciones intr&#237;nsecas _interlockedbittestandset
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Generar una instrucción que examina el bit `b` de la dirección `a` y devuelve su valor actual antes de establecerla a 1.  
  
## Sintaxis  
  
```  
unsigned char _interlockedbittestandset(    long *a,    long b ); unsigned char _interlockedbittestandset_acq(    long *a,    long b ); unsigned char _interlockedbittestandset_HLEAcquire(    long *a,    long b ); unsigned char _interlockedbittestandset_HLERelease(    long *a,    long b ); unsigned char _interlockedbittestandset_nf(    long *a,    long b ); unsigned char _interlockedbittestandset_rel(    long *a,    long b ); unsigned char _interlockedbittestandset64(    __int64 *a,    __int64 b ); unsigned char _interlockedbittestandset64_HLEAcquire(    __int64 *a,    __int64 b ); unsigned char _interlockedbittestandset64_HLERelease(    __int64 *a,    __int64 b );  
```  
  
#### Parámetros  
 \[in\] `a`  
 Puntero a la memoria que se va a examinar.  
  
 \[in\] `b`  
 La posición de bit que se va a probar.  
  
## Valor devuelto  
 El valor del bit en la posición `b` antes de establecerse.  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|Header|  
|------------------------|------------------|------------|  
|`_interlockedbittestandset`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_interlockedbittestandset_acq`, `_interlockedbittestandset_nf`, `_interlockedbittestandset_rel`|ARM|\<intrin.h\>|  
|`_interlockedbittestandset_HLEAcquire`, `_interlockedbittestandset_HLERelease`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h\>|  
|`_interlockedbittestandset64`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_interlockedbittestandset64_HLEAcquire`, `_interlockedbittestandset64_HLERelease`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h\>|  
  
## Comentarios  
 En x86 y procesadores [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)], estos intrínsecos usan la instrucción `lock bts` para leer y establecer el bit especificado en 1.  La operación es atómica.  
  
 En procesadores ARM, utilice los intrínsecos con sufijos `_acq` y `_rel` para adquirir y liberar semántica, como al principio y al final de una sección crítica.  Los intrínsecos ARM con un sufijo `_nf` \("sin límite"\) no actúan como una barrera de memoria.  
  
 En las plataformas de Intel que admiten instrucciones de Elisión de bloqueo de Hardware \(HLE\), los intrínsecos con sufijos `_HLEAcquire` y `_HLERelease` incluyen una sugerencia para el procesador que puede acelerar el rendimiento mediante la eliminación de un paso de escritura de bloqueo en el hardware.  Si se llama a estos intrínsecos en procesadores que no son compatibles con HLE, se omite la sugerencia.  
  
 Estas rutinas solo están disponibles como intrínsecos.  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [Conflictos con el compilador de x86](../build/conflicts-with-the-x86-compiler.md)