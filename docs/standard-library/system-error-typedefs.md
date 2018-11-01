---
title: Definiciones de tipo de &lt;system_error&gt;
ms.date: 11/04/2016
f1_keywords:
- system_error/std::generic_errno
ms.assetid: 28cf9f7d-9c28-4baa-a297-67c8260b07fb
ms.openlocfilehash: 95b2cb22d4fbff4f92cf28041e70ae599c318cbc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531067"
---
# <a name="ltsystemerrorgt-typedefs"></a>Definiciones de tipo de &lt;system_error&gt;

||
|-|
|[generic_errno](#generic_errno)|

## <a name="generic_errno"></a>  generic_errno

Un tipo que representa la enumeración que proporciona los nombres simbólicos para todas las macros de código de error definidas por Posix en `<errno.h>`.

```cpp
typedef errc generic_error;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de [errc](../standard-library/system-error-enums.md#errc).

## <a name="see-also"></a>Vea también

[<system_error>](../standard-library/system-error.md)<br/>
