---
title: "Alineaci&#243;n de malloc | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a8d1d1b4-5122-456f-9a64-a50e105e55a5
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Alineaci&#243;n de malloc
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[malloc](../c-runtime-library/reference/malloc.md) se garantiza para devolver memoria que se alinee correctamente para almacenar cualquier objeto que tenga una alineación fundamental y que podría ajustarse a la cantidad de memoria asignada.  Una *alineación fundamental* es una alineación que es menor o igual que la alineación mayor compatible con la implementación sin una especificación de alineación. \(En Visual C\+\+, esta es la alineación necesaria para `double` u 8 bytes.  En el código destinado a plataformas de 64 bits, son 16 bytes\). Por ejemplo, una asignación de cuatro bytes se alinearía en un límite que admite un objeto de cuatro bytes o más pequeño.  
  
 Visual C\+\+ permite tipos que tienen *alineación extendida*, que también se denominan tipos *demasiado alineados*.  Por ejemplo, los tipos SSE [\_\_m128](../cpp/m128.md) y `__m256`, y los tipos que se declaran con `__declspec(align(``n``))` donde `n` es mayor que 8, tienen alineación extendida.  La alineación en memoria en un límite adecuado para un objeto que requiere alineación extendida no está garantizada por `malloc`.  Para asignar memoria para los tipos demasiado alineados, utilice [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) y las funciones relacionadas.  
  
## Vea también  
 [Uso de las pilas](../build/stack-usage.md)   
 [align](../cpp/align-cpp.md)   
 [\_\_declspec](../cpp/declspec.md)