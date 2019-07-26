---
title: '&lt;cassert&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cassert>
helpviewer_keywords:
- cassert header
ms.assetid: 6ead15a3-ac45-4075-be8e-350bca995c26
ms.openlocfilehash: 58ebd91fb4fa32cf31d2c49429d0445b92fe0c82
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449906"
---
# <a name="ltcassertgt"></a>&lt;cassert&gt;

Incluye el encabezado \<de la biblioteca estándar de C Assert. h > y agrega los `std` nombres asociados al espacio de nombres. Incluir este encabezado garantiza que los nombres declarados mediante vinculación externa en el encabezado de la biblioteca estándar `std` de C se declaran en el espacio de nombres.

> [!NOTE]
> \<Assert. h > no define `static_assert` la macro.

## <a name="syntax"></a>Sintaxis

```cpp
#include <cassert>
```

## <a name="macros"></a>Macros

```cpp
#define assert(E)
```

### <a name="remarks"></a>Comentarios

`assert(E)`es solo constante, si NDEBUG se define donde `assert` se define o se vuelve a definir por última vez o *se convierte en* bool como **true**.

## <a name="see-also"></a>Vea también

[assert Macro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)\
[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
