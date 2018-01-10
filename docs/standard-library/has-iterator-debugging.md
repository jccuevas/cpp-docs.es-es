---
title: _HAS_ITERATOR_DEBUGGING | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _HAS_ITERATOR_DEBUGGING
dev_langs: C++
helpviewer_keywords: _HAS_ITERATOR_DEBUGGING
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7c680338fa84fa0f00e01ea4612d07c851570a36
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="hasiteratordebugging"></a>_HAS_ITERATOR_DEBUGGING  
  
Reemplazada por [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), esta macro define si la característica de depuración del iterador está habilitada en una compilación de depuración. De manera predeterminada, la depuración de iteradores está habilitada en las compilaciones de depuración y deshabilitada en las compilaciones comerciales. Para obtener más información, vea [Compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md).  
  
> [!IMPORTANT]
> El uso directo de la macro `_HAS_ITERATOR_DEBUGGING` está en desuso. En su lugar, use `_ITERATOR_DEBUG_LEVEL` para controlar la configuración de depuración de iteradores. Para obtener más información, vea [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).  
  
## <a name="remarks"></a>Comentarios  
Para habilitar la depuración del iterador en compilaciones de depuración, establezca `_ITERATOR_DEBUG_LEVEL` en 2. Esto es equivalente a una configuración `_HAS_ITERATOR_DEBUGGING` de 1 o habilitado:  
  
```  
#define _ITERATOR_DEBUG_LEVEL 2  
```  
  
`_ITERATOR_DEBUG_LEVEL` no se puede establecer en 2 (y `_HAS_ITERATOR_DEBUGGING` no se puede establecer en 1) en compilaciones comerciales.  
  
Para deshabilitar los iteradores de depuración en compilaciones de depuración, establezca `_ITERATOR_DEBUG_LEVEL` en 0 o 1. Esto es equivalente a una configuración `_HAS_ITERATOR_DEBUGGING` de 0 o deshabilitado:  
  
```  
#define _ITERATOR_DEBUG_LEVEL 0  
```  
  
## <a name="see-also"></a>Vea también  
 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)   
 [Compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md)   
 [Iteradores comprobados](../standard-library/checked-iterators.md)   
 [Bibliotecas seguras: Biblioteca estándar de C++](../standard-library/safe-libraries-cpp-standard-library.md)

