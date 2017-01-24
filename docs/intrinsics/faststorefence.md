---
title: "__faststorefence | Microsoft Docs"
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
  - "__faststorefence_cpp"
  - "__faststorefence"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__faststorefence intrinsic"
  - "sfence instruction"
ms.assetid: 6c6eb973-3cf0-4306-b3af-cfde9b0210a5
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __faststorefence
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Garantiza que cada referencia de memoria anterior, incluidas las referencias de memoria de almacenamiento y de carga, sea visible globalmente antes que cualquier referencia de memoria posterior.  
  
## Sintaxis  
  
```  
void __faststorefence();  
```  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|  
|------------------------|------------------|  
|`__faststorefence`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Genera una secuencia de instrucciones de barrera de memoria completa que garantiza que las operaciones de almacenamiento y de carga emitidas antes que esta función intrínseca sean visibles globalmente antes de que continúe la ejecución.  El efecto es comparable a la función intrínseca `_mm_mfence` en todas plataformas x64, pero más rápido.  
  
 En la plataforma AMD64, esta rutina genera una instrucción que actúa como una barrera de almacenamiento más rápida que la instrucción `sfence`.  Para código crítico en el tiempo, use esta función intrínseca en lugar de `_mm_sfence` únicamente en plataformas AMD64.  En plataformas Intel x64, la instrucción `_mm_sfence` es más rápida.  
  
 Esta rutina solo está disponible como función intrínseca.  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)