---
title: "Funciones intr&#237;nsecas _InterlockedIncrement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_InterlockedIncrement_acq"
  - "_InterlockedIncrement16_rel_cpp"
  - "_InterlockedIncrement16_cpp"
  - "_InterlockedIncrement64_rel"
  - "_InterlockedIncrement_rel"
  - "_InterlockedIncrement64_nf"
  - "_InterlockedIncrement16_acq_cpp"
  - "_InterlockedIncrement_rel_cpp"
  - "_InterlockedIncrement64"
  - "_InterlockedIncrement64_rel_cpp"
  - "_InterlockedIncrement16_nf"
  - "_InterlockedIncrement16_rel"
  - "_InterlockedIncrement16_acq"
  - "_InterlockedIncrement_nf"
  - "_InterlockedIncrement_acq_cpp"
  - "_InterlockedIncrement64_cpp"
  - "_InterlockedIncrement64_acq_cpp"
  - "_InterlockedIncrement"
  - "_InterlockedIncrement_cpp"
  - "_InterlockedIncrement64_acq"
  - "_InterlockedIncrement16"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Intrínseco _InterlockedIncrement"
  - "Intrínseco _InterlockedIncrement_acq"
  - "Intrínseco _InterlockedIncrement_nf"
  - "Intrínseco _InterlockedIncrement_rel"
  - "Intrínseco _InterlockedIncrement16"
  - "Intrínseco _InterlockedIncrement16_acq"
  - "Intrínseco _InterlockedIncrement16_nf"
  - "Intrínseco _InterlockedIncrement16_rel"
  - "Intrínseco _InterlockedIncrement64"
  - "Intrínseco _InterlockedIncrement64_acq"
  - "Intrínseco _InterlockedIncrement64_nf"
  - "Intrínseco _InterlockedIncrement64_rel"
  - "Intrínseco InterlockedIncrement"
  - "Intrínseco InterlockedIncrement_acq"
  - "Intrínseco InterlockedIncrement_rel"
  - "Intrínseco InterlockedIncrement16"
  - "Intrínseco InterlockedIncrement64"
  - "Intrínseco InterlockedIncrement64_acq"
  - "Intrínseco InterlockedIncrement64_rel"
ms.assetid: 37700615-f372-438b-bcef-d76e11839482
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# Funciones intr&#237;nsecas _InterlockedIncrement
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Proporciona compatibilidad intrínseca con el compilador para la función [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] [InterlockedIncrement](http://msdn.microsoft.com/library/ms683614.aspx) de Win32.  
  
## Sintaxis  
  
```  
long _InterlockedIncrement(  
   long * lpAddend  
);  
long _InterlockedIncrement_acq(  
   long * lpAddend  
);  
long _InterlockedIncrement_rel(  
   long * lpAddend  
);  
long _InterlockedIncrement_nf(  
   long * lpAddend  
);  
short _InterlockedIncrement16(  
   short * lpAddend  
);  
short _InterlockedIncrement16_acq(  
   short * lpAddend  
);  
short _InterlockedIncrement16_rel(  
   short * lpAddend  
);  
short _InterlockedIncrement16_nf (  
   short * lpAddend  
);  
__int64 _InterlockedIncrement64(  
   __int64 * lpAddend  
);  
__int64 _InterlockedIncrement64_acq(  
   __int64 * lpAddend  
);  
__int64 _InterlockedIncrement64_rel(  
   __int64 * lpAddend  
);   
__int64 _InterlockedIncrement64_nf(  
   __int64 * lpAddend  
);  
```  
  
#### Parámetros  
 \[in, out\] `lpAddend`  
 Puntero a la variable que se va a incrementar.  
  
## Valor devuelto  
 El valor devuelto es el valor incrementado resultante.  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|Encabezado|  
|------------------------|------------------|----------------|  
|`_InterlockedIncrement`, `_InterlockedIncrement16`, `_InterlockedIncrement64`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedIncrement_acq`, `_InterlockedIncrement_rel`, `_InterlockedIncrement_nf`, `_InterlockedIncrement16_acq`, `_InterlockedIncrement16_rel`, `_InterlockedIncrement16_nf`, `_InterlockedIncrement64_acq`, `_InterlockedIncrement64_rel`, `_InterlockedIncrement64_nf`|ARM|\<intrin.h\>|  
  
## Comentarios  
 Hay diversas variaciones en `_InterlockedIncrement` que varían en función de los tipos de datos que implican y de si se utiliza la liberación o la adquisición de semántica específica del procesador.  
  
 Mientras que la función `_InterlockedIncrement` opera con valores enteros de 32 bits, `_InterlockedIncrement16` opera con valores enteros de 16 bits y `_InterlockedIncrement64` opera con valores enteros de 64 bits.  
  
 En plataformas ARM, utilice los intrínsecos con sufijos `_acq` y `_rel` si necesita adquirir y liberar semántica, como al principio y al final de una sección crítica.  Los intrínsecos con un sufijo `_nf` \("sin límite"\) no actúan como una barrera de memoria.  
  
 La variable a la que apunta el parámetro `lpAddend` debe estar alineada en un límite de 32 bits; de lo contrario, esta función produce un error en sistemas x86 multiprocesadores y en sistemas que no son x86.  Para obtener más información, consulte [alinear](../cpp/align-cpp.md).  
  
 La función de Win32 se declara en `Wdm.h` o `Ntddk.h`.  
  
 Estas rutinas solo están disponibles como intrínsecos.  
  
## Ejemplo  
 Para ver un ejemplo de cómo usar `_InterlockedIncrement`, consulte [\_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [Conflictos con el compilador de x86](../build/conflicts-with-the-x86-compiler.md)