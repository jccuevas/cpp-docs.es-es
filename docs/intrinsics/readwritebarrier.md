---
title: "_ReadWriteBarrier | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_ReadWriteBarrier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ReadWriteBarrier (intrínseco)"
  - "ReadWriteBarrier (intrínseco)"
ms.assetid: dd9f58b5-8bb6-494e-bb0f-9fe184f3908d
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# _ReadWriteBarrier
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Limita las optimizaciones del compilador que pueden reordenar las operaciones de acceso a memoria en el punto de la llamada.  
  
> [!CAUTION]
>  Los objetos `_ReadBarrier`, `_WriteBarrier` y `_ReadWriteBarrier` intrínsecos del compilador y la macro `MemoryBarrier` están desusados y no se deben usar.  Para la comunicación entre subprocesos, use mecanismos como [atomic\_thread\_fence](../Topic/atomic_thread_fence%20Function.md) y [std::atomic\<T\>](../standard-library/atomic.md), definidos en la [Biblioteca estándar de C\+\+](../standard-library/cpp-standard-library-reference.md).  Para el acceso de hardware, utilice la opción del compilador [\/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) junto con la palabra clave [volatile](../cpp/volatile-cpp.md).  
  
## Sintaxis  
  
```  
void _ReadWriteBarrier(void);  
```  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|  
|------------------------|------------------|  
|`_ReadWriteBarrier`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 El objeto `_ReadWriteBarrier` intrínseco limita las optimizaciones del compilador que pueden quitar o reordenar las operaciones de acceso a memoria en el punto de la llamada.  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [\_ReadBarrier](../intrinsics/readbarrier.md)   
 [\_WriteBarrier](../intrinsics/writebarrier.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)