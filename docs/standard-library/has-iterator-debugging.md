---
title: _HAS_ITERATOR_DEBUGGING
ms.date: 11/04/2016
f1_keywords:
- _HAS_ITERATOR_DEBUGGING
helpviewer_keywords:
- _HAS_ITERATOR_DEBUGGING
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
ms.openlocfilehash: a1e3017ed7c6def18ce02d99dc8253b69c11ab58
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448830"
---
# <a name="hasiteratordebugging"></a>_HAS_ITERATOR_DEBUGGING

Reemplazada por [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), esta macro define si la característica de depuración del iterador está habilitada en una compilación de depuración. De manera predeterminada, la depuración de iteradores está habilitada en las compilaciones de depuración y deshabilitada en las compilaciones comerciales. Para obtener más información, vea [Compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md).

> [!IMPORTANT]
> El uso directo de la macro _HAS_ITERATOR_DEBUGGING está en desuso. En su lugar, use _ITERATOR_DEBUG_LEVEL para controlar la configuración de depuración del iterador. Para obtener más información, vea [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Comentarios

Para habilitar la depuración de iteradores en las compilaciones de depuración, establezca _ITERATOR_DEBUG_LEVEL en 2. Es equivalente a un valor _HAS_ITERATOR_DEBUGGING de 1 o habilitado:

```cpp
#define _ITERATOR_DEBUG_LEVEL 2
```

_ITERATOR_DEBUG_LEVEL no se puede establecer en 2 (y _HAS_ITERATOR_DEBUGGING no se puede establecer en 1) en las compilaciones comerciales.

Para deshabilitar los iteradores de depuración en las compilaciones de depuración, establezca _ITERATOR_DEBUG_LEVEL en 0 o 1. Es equivalente a un valor _HAS_ITERATOR_DEBUGGING de 0 o deshabilitado:

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

## <a name="see-also"></a>Vea también

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)\
[Compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md)\
[Iteradores comprobados](../standard-library/checked-iterators.md)\
[Bibliotecas seguras: biblioteca estándar de C++](../standard-library/safe-libraries-cpp-standard-library.md)
