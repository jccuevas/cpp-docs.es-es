---
title: _SECURE_SCL
ms.date: 11/04/2016
f1_keywords:
- _SECURE_SCL
helpviewer_keywords:
- _SECURE_SCL
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
ms.openlocfilehash: dcfaee2906136dffbe79a49f089a079104112e78
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559164"
---
# <a name="securescl"></a>_SECURE_SCL

Reemplazada por [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), esta macro define los [iteradores activados](../standard-library/checked-iterators.md) están habilitados. De forma predeterminada, los iteradores activados están habilitados en las compilaciones de depuración y deshabilitados en las compilaciones comerciales.

> [!IMPORTANT]
> Uso directo de la macro _SECURE_SCL está en desuso. En su lugar, use _ITERATOR_DEBUG_LEVEL al control comprueba la configuración de iteradores. Para obtener más información, vea [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Comentarios

Cuando los iteradores activados están habilitados, el uso de iteradores no seguros produce un error en tiempo de ejecución y finaliza el programa. Para habilitar los iteradores activados, establezca _ITERATOR_DEBUG_LEVEL en 1 o 2. Esto es equivalente al valor _SECURE_SCL 1 o habilitado:

```cpp
#define _ITERATOR_DEBUG_LEVEL 1
```

Para deshabilitar los iteradores activados, establezca _ITERATOR_DEBUG_LEVEL en 0. Esto es equivalente a una configuración _SECURE_SCL 0 o deshabilitado:

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

Para obtener más información sobre cómo deshabilitar las advertencias sobre iteradores comprobados, vea [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

## <a name="see-also"></a>Vea también

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)<br/>
[Checked Iterators](../standard-library/checked-iterators.md)<br/>
[Debug Iterator Support](../standard-library/debug-iterator-support.md)<br/>
[Bibliotecas seguras: Biblioteca estándar de C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
