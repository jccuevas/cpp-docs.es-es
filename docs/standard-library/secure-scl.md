---
title: _SECURE_SCL | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _SECURE_SCL
dev_langs:
- C++
helpviewer_keywords:
- _SECURE_SCL
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b49e101e944d4309a1d05e605a49452d9e17083c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="securescl"></a>_SECURE_SCL
  
Reemplazada por [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), esta macro define los [iteradores activados](../standard-library/checked-iterators.md) están habilitados. De forma predeterminada, los iteradores activados están habilitados en las compilaciones de depuración y deshabilitados en las compilaciones comerciales.  
  
> [!IMPORTANT]
> El uso directo de la macro `_SECURE_SCL` está en desuso. En su lugar, use `_ITERATOR_DEBUG_LEVEL` para controlar la configuración de iteradores activados. Para más información, vea [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).  
  
## <a name="remarks"></a>Comentarios  
  
Cuando los iteradores activados están habilitados, el uso de iteradores no seguros produce un error en tiempo de ejecución y finaliza el programa. Para habilitar los iteradores activados, establezca `_ITERATOR_DEBUG_LEVEL` en 1 o 2. Esto es equivalente a una configuración de `_SECURE_SCL` de 1 o habilitado:  
  
```  
#define _ITERATOR_DEBUG_LEVEL 1  
```  
  
Para deshabilitar los iteradores activados, establezca `_ITERATOR_DEBUG_LEVEL` en 0. Esto es equivalente a una configuración de `_SECURE_SCL` de 0 o deshabilitado:  
  
```  
#define _ITERATOR_DEBUG_LEVEL 0  
```  
  
Para más información sobre cómo deshabilitar las advertencias sobre iteradores activados, vea [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).  
  
## <a name="see-also"></a>Vea también  
[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)   
[Iteradores activados](../standard-library/checked-iterators.md)   
[Compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md)   
[Bibliotecas seguras: Biblioteca estándar de C++](../standard-library/safe-libraries-cpp-standard-library.md)

