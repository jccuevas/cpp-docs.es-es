---
title: include()
ms.date: 10/18/2018
f1_keywords:
- include()
helpviewer_keywords:
- include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
ms.openlocfilehash: 1208f14a9f6b3724dd5353df57213baa3910d07f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59040932"
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

**Específicos de C++: END**

## <a name="see-also"></a>Vea también

[Atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)