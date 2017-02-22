---
title: "_SECURE_SCL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_SECURE_SCL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_SECURE_SCL"
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# _SECURE_SCL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define si [Iteradores activados](../standard-library/checked-iterators.md) está habilitado.  Si se define como 1, el uso no seguro de iterador produce un error en tiempo de ejecución y se finaliza el programa.  Si se define como 0, se deshabilitan los iteradores comprobados.  En modo de depuración, el valor predeterminado de **\_SECURE\_SCL** es 1, lo que significa que los iteradores comprobados están habilitados.  En modo de lanzamiento, el valor predeterminado de `_SECURE_SCL` es 0.  
  
> [!IMPORTANT]
>  Uso `_ITERATOR_DEBUG_LEVEL` de controlar `_SECURE_SCL`.  Para obtener más información, vea [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md).  
  
## Comentarios  
 Para habilitar comprobó iteradores, establezca **\_SECURE\_SCL** a 1:  
  
```  
#define _SECURE_SCL 1  
```  
  
 Para deshabilitar comprobó iteradores, establezca **\_SECURE\_SCL** a 0:  
  
```  
#define _SECURE_SCL 0  
```  
  
 Para obtener información sobre cómo deshabilitar advertencias sobre iteradores comprobados, vea [\_SCL\_SECURE\_NO\_WARNINGS](../standard-library/scl-secure-no-warnings.md).  
  
## Vea también  
 [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md)   
 [Iteradores activados](../standard-library/checked-iterators.md)   
 [Compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md)   
 [Bibliotecas seguras: Biblioteca estándar de C\+\+](../standard-library/safe-libraries-cpp-standard-library.md)