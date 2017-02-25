---
title: "_HAS_ITERATOR_DEBUGGING | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_HAS_ITERATOR_DEBUGGING"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_HAS_ITERATOR_DEBUGGING"
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# _HAS_ITERATOR_DEBUGGING
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define si la característica de depuración de iterador está habilitada en una compilación de depuración.  De forma predeterminada, se habilita la depuración del iterador.  Para obtener más información, vea [Compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md).  
  
> [!IMPORTANT]
>  Uso `_ITERATOR_DEBUG_LEVEL` de controlar `_HAS_ITERATOR_DEBUGGING`.  Para obtener más información, vea [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md).  
  
## Comentarios  
 Para habilitar la depuración de iterador en las compilaciones de depuración, establezca **\_HAS\_ITERATOR\_DEBUGGING** a 1:  
  
```  
#define _HAS_ITERATOR_DEBUGGING 1  
```  
  
 **\_HAS\_ITERATOR\_DEBUGGING** no puede establecerse en 1 en versiones comerciales.  
  
 Para deshabilitar la depuración de iterador en las compilaciones de depuración, establezca **\_HAS\_ITERATOR\_DEBUGGING** a 0:  
  
```  
#define _HAS_ITERATOR_DEBUGGING 0  
```  
  
## Vea también  
 [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md)   
 [Compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md)   
 [Iteradores activados](../standard-library/checked-iterators.md)   
 [Bibliotecas seguras: Biblioteca estándar de C\+\+](../standard-library/safe-libraries-cpp-standard-library.md)