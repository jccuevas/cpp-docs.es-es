---
title: include() | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- include()
dev_langs:
- C++
helpviewer_keywords:
- include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 756aea4400d98b2bf061a54955b3df4b4eddd993
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="include"></a>include()
**Específicos de C++**  
  
 Deshabilita la exclusión automática.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
include("Name1"[,"Name2", ...])  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Name1`  
 Primer elemento que se incluirá forzosamente.  
  
 `Name2`  
 Segundo elemento que se incluirá forzosamente (si es necesario).  
  
## <a name="remarks"></a>Comentarios  
 Las bibliotecas de tipos pueden incluir definiciones de elementos definidos en encabezados de sistema u otras bibliotecas de tipos. `#import` intenta evitar varios errores de definición mediante la exclusión automática de dichos elementos. Si los elementos se han excluido, como se indica por [C4192 de advertencia del compilador (nivel 3)](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md), y que no deberían tener estado, este atributo se puede usar para deshabilitar la exclusión automática. Este atributo puede tomar cualquier número de argumentos, siendo cada uno el nombre del elemento de la biblioteca de tipos que se incluirá.  
  
 **FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)