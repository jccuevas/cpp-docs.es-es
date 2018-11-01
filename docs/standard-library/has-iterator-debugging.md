---
title: _HAS_ITERATOR_DEBUGGING
ms.date: 11/04/2016
f1_keywords:
- _HAS_ITERATOR_DEBUGGING
helpviewer_keywords:
- _HAS_ITERATOR_DEBUGGING
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
ms.openlocfilehash: 339c32f9b487db2e318f8763ac01a0d155fc1dc1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575882"
---
# <a name="hasiteratordebugging"></a>_HAS_ITERATOR_DEBUGGING

Reemplazada por [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), esta macro define si la característica de depuración del iterador está habilitada en una compilación de depuración. De manera predeterminada, la depuración de iteradores está habilitada en las compilaciones de depuración y deshabilitada en las compilaciones comerciales. Para obtener más información, vea [Compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md).

> [!IMPORTANT]
> Uso directo de la macro _HAS_ITERATOR_DEBUGGING está en desuso. En su lugar, use _ITERATOR_DEBUG_LEVEL para controlar la configuración de depuración de iterador. Para obtener más información, vea [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Comentarios

Para habilitar la depuración en compilaciones de depuración del iterador, establezca _ITERATOR_DEBUG_LEVEL a 2. Esto es equivalente a una configuración _HAS_ITERATOR_DEBUGGING de 1 o habilitado:

```cpp
#define _ITERATOR_DEBUG_LEVEL 2
```

_ITERATOR_DEBUG_LEVEL no puede establecerse en 2 (y _HAS_ITERATOR_DEBUGGING no se puede establecer en 1) en compilaciones comerciales.

Para deshabilitar los iteradores de depuración en compilaciones de depuración, establezca _ITERATOR_DEBUG_LEVEL en 0 o 1. Esto es equivalente a una configuración _HAS_ITERATOR_DEBUGGING 0 o deshabilitado:

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

## <a name="see-also"></a>Vea también

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)<br/>
[Debug Iterator Support](../standard-library/debug-iterator-support.md)<br/>
[Checked Iterators](../standard-library/checked-iterators.md)<br/>
[Bibliotecas seguras: Biblioteca estándar de C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
