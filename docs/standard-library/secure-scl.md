---
title: _SECURE_SCL
ms.date: 11/04/2016
f1_keywords:
- _SECURE_SCL
helpviewer_keywords:
- _SECURE_SCL
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
ms.openlocfilehash: 1af084363fc0d6d1723a9af7b633779f92ed2b38
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450540"
---
# <a name="securescl"></a>_SECURE_SCL

Reemplazada por [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), esta macro define los [iteradores activados](../standard-library/checked-iterators.md) están habilitados. De forma predeterminada, los iteradores activados están habilitados en las compilaciones de depuración y deshabilitados en las compilaciones comerciales.

> [!IMPORTANT]
> El uso directo de la macro _SECURE_SCL está en desuso. En su lugar, use _ITERATOR_DEBUG_LEVEL para controlar la configuración de iterador comprobado. Para obtener más información, vea [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Comentarios

Cuando los iteradores activados están habilitados, el uso de iteradores no seguros produce un error en tiempo de ejecución y finaliza el programa. Para habilitar los iteradores comprobados, establezca _ITERATOR_DEBUG_LEVEL en 1 o 2. Es equivalente a un valor _SECURE_SCL de 1 o habilitado:

```cpp
#define _ITERATOR_DEBUG_LEVEL 1
```

Para deshabilitar los iteradores comprobados, establezca _ITERATOR_DEBUG_LEVEL en 0. Es equivalente a un valor _SECURE_SCL de 0 o deshabilitado:

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

Para obtener más información sobre cómo deshabilitar las advertencias sobre iteradores comprobados, vea [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

## <a name="see-also"></a>Vea también

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)\
[Iteradores activados](../standard-library/checked-iterators.md)\
[Compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md)\
[Bibliotecas seguras: biblioteca estándar de C++](../standard-library/safe-libraries-cpp-standard-library.md)
