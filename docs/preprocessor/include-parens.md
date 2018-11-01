---
title: include()
ms.date: 10/18/2018
f1_keywords:
- include()
helpviewer_keywords:
- include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
ms.openlocfilehash: 8f3227ba49cc0928fec5d5917efcd8869982d94a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599750"
---
# <a name="include"></a>include()

**Específicos de C++**

Deshabilita la exclusión automática.

## <a name="syntax"></a>Sintaxis

```
include("Name1"[,"Name2", ...])
```

### <a name="parameters"></a>Parámetros

*Nombre1*<br/>
Primer elemento que se incluirá forzosamente.

*Nombre2*<br/>
Segundo elemento que se incluirá forzosamente (si es necesario).

## <a name="remarks"></a>Comentarios

Las bibliotecas de tipos pueden incluir definiciones de elementos definidos en encabezados de sistema u otras bibliotecas de tipos. `#import` intenta evitar varios errores de definición mediante la exclusión automática de dichos elementos. Si se han excluido elementos, tal y como indica [advertencia del compilador (nivel 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md), y que no deberían tener estado, este atributo se puede usar para deshabilitar la exclusión automática. Este atributo puede tomar cualquier número de argumentos, siendo cada uno el nombre del elemento de la biblioteca de tipos que se incluirá.

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)