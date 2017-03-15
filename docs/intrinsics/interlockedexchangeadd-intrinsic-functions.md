---
title: "Funciones intr&#237;nsecas _InterlockedExchangeAdd | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_InterlockedExchangeAdd64_nf"
  - "_InterlockedExchangeAdd64_rel"
  - "_InterlockedExchangeAdd16_rel"
  - "_InterlockedExchangeAdd_acq"
  - "_InterlockedExchangeAdd_nf"
  - "_InterlockedExchangeAdd_rel"
  - "_InterlockedExchangeAdd8_acq"
  - "_InterlockedExchangeAdd16_nf"
  - "_InterlockedExchangeAdd_acq_cpp"
  - "_InterlockedExchangeAdd64_acq_cpp"
  - "_InterlockedExchangeAdd16_acq"
  - "_InterlockedExchangeAdd_HLERelease"
  - "_InterlockedExchangeAdd64_cpp"
  - "_InterlockedExchangeAdd64_HLERelease"
  - "_InterlockedExchangeAdd64_acq"
  - "_InterlockedExchangeAdd8"
  - "_InterlockedExchangeAdd64"
  - "_InterlockedExchangeAdd8_nf"
  - "_InterlockedExchangeAdd16"
  - "_InterlockedExchangeAdd64_rel_cpp"
  - "_InterlockedExchangeAdd_cpp"
  - "_InterlockedExchangeAdd8_rel"
  - "_InterlockedExchangeAdd_HLEAcquire"
  - "_InterlockedExchangeAdd64_HLEAcquire"
  - "_InterlockedExchangeAdd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Intrínseco _InterlockedExchangeAdd"
  - "Intrínseco _InterlockedExchangeAdd_acq"
  - "Intrínseco _InterlockedExchangeAdd_HLEAcquire"
  - "Intrínseco _InterlockedExchangeAdd_HLERelease"
  - "Intrínseco _InterlockedExchangeAdd_nf"
  - "Intrínseco _InterlockedExchangeAdd_rel"
  - "Intrínseco _InterlockedExchangeAdd16"
  - "Intrínseco _InterlockedExchangeAdd16_acq"
  - "Intrínseco _InterlockedExchangeAdd16_nf"
  - "Intrínseco _InterlockedExchangeAdd16_rel"
  - "Intrínseco _InterlockedExchangeAdd64"
  - "Intrínseco _InterlockedExchangeAdd64_acq"
  - "Intrínseco _InterlockedExchangeAdd64_HLEAcquire"
  - "Intrínseco _InterlockedExchangeAdd64_HLERelease"
  - "Intrínseco _InterlockedExchangeAdd64_nf"
  - "Intrínseco _InterlockedExchangeAdd64_rel"
  - "Intrínseco _InterlockedExchangeAdd8"
  - "Intrínseco _InterlockedExchangeAdd8_acq"
  - "Intrínseco _InterlockedExchangeAdd8_nf"
  - "Intrínseco _InterlockedExchangeAdd8_rel"
  - "Intrínseco InterlockedExchangeAdd"
  - "Intrínseco InterlockedExchangeAdd_acq"
  - "Intrínseco InterlockedExchangeAdd_rel"
  - "Intrínseco InterlockedExchangeAdd64"
  - "Intrínseco InterlockedExchangeAdd64_acq"
  - "Intrínseco InterlockedExchangeAdd64_rel"
ms.assetid: 25809e1f-9c60-4492-9f7c-0fb59c8d13d2
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# Funciones intr&#237;nsecas _InterlockedExchangeAdd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Proporcionar compatibilidad con intrínsecos del compilador para la función [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] [\_InterlockedExchangeAdd Intrinsic Functions](../intrinsics/interlockedexchangeadd-intrinsic-functions.md) de Win32.  
  
## Sintaxis  
  
```  
long _InterlockedExchangeAdd(    long volatile * Addend,    long Value ); long _InterlockedExchangeAdd_acq(    long volatile * Addend,    long Value ); long _InterlockedExchangeAdd_rel(    long volatile * Addend,    long Value ); long _InterlockedExchangeAdd_nf(    long volatile * Addend,    long Value ); long _InterlockedExchangeAdd_HLEAcquire(    long volatile * Addend,    long Value ); long _InterlockedExchangeAdd_HLERelease(    long volatile * Addend,    long Value ); char _InterlockedExchangeAdd8(    char volatile * Addend,    char Value ); char _InterlockedExchangeAdd8_acq(    char volatile * Addend,    char Value ); char _InterlockedExchangeAdd8_rel(    char volatile * Addend,    char Value ); char _InterlockedExchangeAdd8_nf(    char volatile * Addend,    char Value ); short _InterlockedExchangeAdd16(    short volatile * Addend,    short Value ); short _InterlockedExchangeAdd16_acq(    short volatile * Addend,    short Value ); short _InterlockedExchangeAdd16_rel(    short volatile * Addend,    short Value ); short _InterlockedExchangeAdd16_nf(    short volatile * Addend,    short Value ); __int64 _InterlockedExchangeAdd64(    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedExchangeAdd64_acq(    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedExchangeAdd64_rel(    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedExchangeAdd64_nf(    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedExchangeAdd64_HLEAcquire(    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedExchangeAdd64_HLERelease(    __int64 volatile * Addend,    __int64 Value );   
```  
  
#### Parámetros  
 \[in, out\] `Addend`  
 El valor al que se agregará; lo reemplaza el resultado de la suma.  
  
 \[in\] `Value`  
 El valor que se va a agregar.  
  
## Valor devuelto  
 El valor devuelto es el valor inicial de la variable a la que apunta el parámetro `Addend`.  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|Header|  
|------------------------|------------------|------------|  
|`_InterlockedExchangeAdd`, `_InterlockedExchangeAdd8`, `_InterlockedExchangeAdd16`, `_InterlockedExchangeAdd64`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedExchangeAdd_acq`, `_InterlockedExchangeAdd_rel`, `_InterlockedExchangeAdd_nf`, `_InterlockedExchangeAdd8_acq`, `_InterlockedExchangeAdd8_rel`, `_InterlockedExchangeAdd8_nf`,`_InterlockedExchangeAdd16_acq`, `_InterlockedExchangeAdd16_rel`, `_InterlockedExchangeAdd16_nf`, `_InterlockedExchangeAdd64_acq`, `_InterlockedExchangeAdd64_rel`, `_InterlockedExchangeAdd64_nf`|ARM|\<intrin.h\>|  
|`_InterlockedExchangeAdd_HLEAcquire`, `_InterlockedExchangeAdd_HLERelease`, `_InterlockedExchangeAdd64_HLEAcquire`, `_InterlockedExchangeAdd64_HLErelease`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h\>|  
  
## Comentarios  
 Hay diversas variaciones en `_InterlockedExchangeAdd` que varían en función de los tipos de datos que implican y de si se utiliza la liberación o la adquisición de semántica específica del procesador.  
  
 Mientras que la función `_InterlockedExchangeAdd` opera con valores enteros de 32 bits, `_InterlockedExchangeAdd8` opera con valores enteros de 8 bits, `_InterlockedExchangeAdd16` opera con valores enteros de 16 bits y `_InterlockedExchangeAdd64` opera con valores enteros de 64 bits.  
  
 En plataformas ARM, utilice los intrínsecos con sufijos `_acq` y `_rel` si necesita adquirir y liberar semántica, como al principio y al final de una sección crítica.  Los intrínsecos con un sufijo `_nf` \("sin límite"\) no actúan como una barrera de memoria.  
  
 En las plataformas de Intel que admiten instrucciones de Elisión de bloqueo de Hardware \(HLE\), los intrínsecos con sufijos `_HLEAcquire` y `_HLERelease` incluyen una sugerencia para el procesador que puede acelerar el rendimiento mediante la eliminación de un paso de escritura de bloqueo en el hardware.  Si se llama a estos intrínsecos en plataformas que no son compatibles con HLE, se omite la sugerencia.  
  
 Estas rutinas solo están disponibles como intrínsecos.  Por lo tanto, son intrínsecos tanto si se usa [\/Oi](../build/reference/oi-generate-intrinsic-functions.md) o el [intrínseco \#pragma](../preprocessor/intrinsic.md) como si no se usa.  No es posible utilizar la [función \#pragma](../preprocessor/function-c-cpp.md) en estos intrínsecos.  
  
## Ejemplo  
 Para ver un ejemplo de cómo usar `_InterlockedExchangeAdd`, consulte [\_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [Conflictos con el compilador de x86](../build/conflicts-with-the-x86-compiler.md)