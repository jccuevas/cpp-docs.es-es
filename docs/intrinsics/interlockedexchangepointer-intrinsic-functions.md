---
title: "Funciones intr&#237;nsecas _InterlockedExchangePointer | Microsoft Docs"
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
  - "_InterlockedExchangePointer_cpp"
  - "_InterlockedExchangePointer_rel"
  - "_InterlockedExchangePointer_nf"
  - "_InterlockedExchangePointer_HLERelease"
  - "_InterlockedExchangePointer_acq"
  - "_InterlockedExchangePointer"
  - "_InterlockedExchangePointer_acq_cpp"
  - "_InterlockedExchangePointer_HLEAcquire"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Intrínseco _InterlockedExchangePointer"
  - "Intrínseco _InterlockedExchangePointer_acq"
  - "Intrínseco _InterlockedExchangePointer_HLEAcquire"
  - "Intrínseco _InterlockedExchangePointer_HLERelease"
  - "Intrínseco _InterlockedExchangePointer_nf"
  - "Intrínseco _InterlockedExchangePointer_rel"
  - "Intrínseco InterlockedExchangePointer"
  - "Intrínseco InterlockedExchangePointer_acq"
ms.assetid: 0eaca0b0-d79e-406b-892d-b3b462c50bbb
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Funciones intr&#237;nsecas _InterlockedExchangePointer
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Realizar una operación de intercambio atómico, que copia la dirección que se pasa como segundo argumento al primero y devuelve la dirección original del primero.  
  
## Sintaxis  
  
```  
void * _InterlockedExchangePointer(    void * volatile * Target,    void * Value );  void * _InterlockedExchangePointer_acq(    void * volatile * Target,    void * Value );  void * _InterlockedExchangePointer_rel(    void * volatile * Target,    void * Value );  void * _InterlockedExchangePointer_nf(    void * volatile * Target,    void * Value );  void * _InterlockedExchangePointer_HLEAcquire(    void * volatile * Target,    void * Value );  void * _InterlockedExchangePointer_HLERelease(    void * volatile * Target,    void * Value );  
```  
  
#### Parámetros  
 \[in, out\] `Target`  
 Puntero al puntero al valor que se va a intercambiar.  La función establece el valor en `Value` y devuelve su valor anterior.  
  
 \[in\] `Value`  
 Valor que se va a intercambiar por el valor al que apunta `Target`.  
  
## Valor devuelto  
 La función devuelve el valor inicial al que apunta `Target`.  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|Header|  
|------------------------|------------------|------------|  
|`_InterlockedExchangePointer`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedExchangePointer_acq`, `_InterlockedExchangePointer_rel`, `_InterlockedExchangePointer_nf`|ARM|\<intrin.h\>|  
|`_InterlockedExchangePointer_HLEAcquire`, `_InterlockedExchangePointer_HLERelease`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] con compatibilidad HLE|\<immintrin.h\>|  
  
 En la arquitectura x86, `_InterlockedExchangePointer` es una macro que llama a `_InterlockedExchange`.  
  
## Comentarios  
 En un sistema de 64 bits, los parámetros son de 64 bits y deben estar alineados en límites de 64 bits; de lo contrario, se produce un error en la función.  En un sistema de 32 bits, los parámetros son de 32 bits y deben estar alineados en límites de 32 bits.  Para obtener más información, consulte [alinear](../cpp/align-cpp.md).  
  
 En plataformas ARM, utilice los intrínsecos con sufijos `_acq` y `_rel` si necesita adquirir y liberar semántica, como al principio y al final de una sección crítica.  El intrínseco con un sufijo `_nf` \("sin límite"\) no actúa como una barrera de memoria.  
  
 En las plataformas de Intel que admiten instrucciones de Elisión de bloqueo de Hardware \(HLE\), los intrínsecos con sufijos `_HLEAcquire` y `_HLERelease` incluyen una sugerencia para el procesador que puede acelerar el rendimiento mediante la eliminación de un paso de escritura de bloqueo en el hardware.  Si se llama a estos intrínsecos en plataformas que no son compatibles con HLE, se omite la sugerencia.  
  
 Estas rutinas solo están disponibles como intrínsecos.  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [Conflictos con el compilador de x86](../build/conflicts-with-the-x86-compiler.md)