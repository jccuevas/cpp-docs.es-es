---
title: no_auto_exclude | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_auto_exclude
dev_langs:
- C++
helpviewer_keywords:
- no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b0c8d28e1e9c7306c1a74db90177caf76ca95b0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="noautoexclude"></a>no_auto_exclude
**Específicos de C++**  
  
 Deshabilita la exclusión automática.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
no_auto_exclude  
```  
  
## <a name="remarks"></a>Comentarios  
 Las bibliotecas de tipos pueden incluir definiciones de elementos definidos en encabezados de sistema u otras bibliotecas de tipos. `#import` intenta evitar varios errores de definición mediante la exclusión automática de dichos elementos. Cuando esto sucede, [C4192 de advertencia del compilador (nivel 3)](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md) se emiten para que cada elemento que se excluirá. Se puede deshabilitar esta exclusión automática con este atributo.  
  
 **FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)