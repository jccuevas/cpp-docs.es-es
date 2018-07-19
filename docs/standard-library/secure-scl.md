---
title: _SECURE_SCL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- _SECURE_SCL
dev_langs:
- C++
helpviewer_keywords:
- _SECURE_SCL
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 88e7153fa77c7a0aa213bfb01587f2ea080c6ddd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854095"
---
# <a name="securescl"></a>_SECURE_SCL

Reemplazada por [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), esta macro define los [iteradores activados](../standard-library/checked-iterators.md) están habilitados. De forma predeterminada, los iteradores activados están habilitados en las compilaciones de depuración y deshabilitados en las compilaciones comerciales.

> [!IMPORTANT]
> El uso directo de la macro `_SECURE_SCL` está en desuso. En su lugar, use `_ITERATOR_DEBUG_LEVEL` para controlar la configuración de iteradores activados. Para más información, vea [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Comentarios

Cuando los iteradores activados están habilitados, el uso de iteradores no seguros produce un error en tiempo de ejecución y finaliza el programa. Para habilitar los iteradores activados, establezca `_ITERATOR_DEBUG_LEVEL` en 1 o 2. Esto es equivalente a una configuración de `_SECURE_SCL` de 1 o habilitado:

```cpp
#define _ITERATOR_DEBUG_LEVEL 1
```

Para deshabilitar los iteradores activados, establezca `_ITERATOR_DEBUG_LEVEL` en 0. Esto es equivalente a una configuración de `_SECURE_SCL` de 0 o deshabilitado:

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

Para obtener más información sobre cómo deshabilitar las advertencias sobre iteradores comprobados, vea [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

## <a name="see-also"></a>Vea también

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)<br/>
[Checked Iterators](../standard-library/checked-iterators.md)<br/>
[Debug Iterator Support](../standard-library/debug-iterator-support.md)<br/>
[Bibliotecas seguras: Biblioteca estándar de C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
