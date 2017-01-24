---
title: "Funciones intr&#237;nsecas _InterlockedCompareExchangePointer | Microsoft Docs"
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
  - "_InterlockedCompareExchangePointer_HLERelease"
  - "_InterlockedCompareExchangePointer_rel"
  - "_InterlockedCompareExchangePointer_acq_cpp"
  - "_InterlockedCompareExchangePointer"
  - "_InterlockedCompareExchangePointer_cpp"
  - "_InterlockedCompareExchangePointer_np"
  - "_InterlockedCompareExchangePointer_rel_cpp"
  - "_InterlockedCompareExchangePointer_HLEAcquire"
  - "_InterlockedCompareExchangePointer_acq"
  - "_InterlockedCompareExchangePointer_nf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Intrínseco _InterlockedCompareExchangePointer"
  - "Intrínseco _InterlockedCompareExchangePointer_acq"
  - "Intrínseco _InterlockedCompareExchangePointer_HLEAcquire"
  - "Intrínseco _InterlockedCompareExchangePointer_HLERelease"
  - "Intrínseco _InterlockedCompareExchangePointer_nf"
  - "Intrínseco _InterlockedCompareExchangePointer_np"
  - "Intrínseco _InterlockedCompareExchangePointer_rel"
  - "Intrínseco InterlockedCompareExchangePointer"
  - "Intrínseco InterlockedCompareExchangePointer_acq"
  - "Intrínseco InterlockedCompareExchangePointer_rel"
ms.assetid: 97fde59d-2bf9-42aa-a0fe-a5b6befdd44b
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Funciones intr&#237;nsecas _InterlockedCompareExchangePointer
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Realiza una operación atómica que almacena la dirección `Exchange` en la dirección `Destination` si `Comparand` y la dirección `Destination` son iguales.  
  
## Sintaxis  
  
```  
void * _InterlockedCompareExchangePointer (    void * volatile * Destination,    void * Exchange,    void * Comparand ); void * _InterlockedCompareExchangePointer_acq (    void * volatile * Destination,    void * Exchange,    void * Comparand ); void * _InterlockedCompareExchangePointer_HLEAcquire (    void * volatile * Destination,    void * Exchange,    void * Comparand ); void * _InterlockedCompareExchangePointer_HLERelease (    void * volatile * Destination,    void * Exchange,    void * Comparand ); void * _InterlockedCompareExchangePointer_nf (    void * volatile * Destination,    void * Exchange,    void * Comparand ); void * _InterlockedCompareExchangePointer_np (    void * volatile * Destination,    void * Exchange,    void * Comparand ); long _InterlockedCompareExchangePointer_rel (    void * volatile * Destination,    void * Exchange,    void * Comparand );  
```  
  
#### Parámetros  
 \[in, out\] `Destination`  
 Puntero a un puntero al valor de destino.  El signo se omite.  
  
 \[in\] `Exchange`  
 Puntero de intercambio.  El signo se omite.  
  
 \[in\] `Comparand`  
 Puntero que se compara con el destino.  El signo se omite.  
  
## Valor devuelto  
 El valor devuelto es el valor inicial del destino.  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|Header|  
|------------------------|------------------|------------|  
|`_InterlockedCompareExchangePointer`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedCompareExchangePointer_acq`, `_InterlockedCompareExchangePointer_nf`, `_InterlockedCompareExchangePointer_rel`|ARM|\<iiintrin.h\>|  
|`_InterlockedCompareExchangePointer_HLEAcquire`, `_InterlockedCompareExchangePointer_HLERelease`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h\>|  
  
## Comentarios  
 `_InterlockedCompareExchangePointer` realiza una comparación atómica de la dirección `Destination` con la dirección `Comparand`.  Si la dirección `Destination` es igual a la dirección `Comparand`, la dirección `Exchange` se almacena en la dirección especificada por `Destination`.  De lo contrario, no se realiza ninguna operación.  
  
 `_InterlockedCompareExchangePointer` proporciona compatibilidad con intrínsecos del compilador para la función [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] [\_InterlockedCompareExchangePointer](http://msdn.microsoft.com/library/ff547863.aspx) de Win32.  
  
 Para ver un ejemplo de cómo usar `_InterlockedCompareExchangePointer`, consulte [\_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).  
  
 En plataformas ARM, utilice los intrínsecos con sufijos `_acq` y `_rel` si necesita adquirir y liberar semántica, como al principio y al final de una sección crítica.  Los intrínsecos ARM con un sufijo `_nf` \("sin límite"\) no actúan como una barrera de memoria.  
  
 Los intrínsecos con un sufijo `_np` \("sin captura previa"\) impiden que el compilador inserte una posible operación de captura previa.  
  
 En las plataformas de Intel que admiten instrucciones de Elisión de bloqueo de Hardware \(HLE\), los intrínsecos con sufijos `_HLEAcquire` y `_HLERelease` incluyen una sugerencia para el procesador que puede acelerar el rendimiento mediante la eliminación de un paso de escritura de bloqueo en el hardware.  Si se llama a estos intrínsecos en plataformas que no son compatibles con HLE, se omite la sugerencia.  
  
 Estas rutinas solo están disponibles como intrínsecos.  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)