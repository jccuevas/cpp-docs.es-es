---
title: '&lt;cassert&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cassert>
helpviewer_keywords:
- cassert header
ms.assetid: 6ead15a3-ac45-4075-be8e-350bca995c26
ms.openlocfilehash: 14dda03e835ec411013b2d827bd1ccaa77f8982e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245017"
---
# <a name="ltcassertgt"></a>&lt;cassert&gt;

Incluye el encabezado de la biblioteca estándar de C \<assert.h > y agrega los nombres asociados a la `std` espacio de nombres. Incluir este encabezado también garantiza que los nombres declarados mediante vinculación externa en el encabezado de la biblioteca estándar de C se declaran en el `std` espacio de nombres.

> [!NOTE]
> \<Assert.h > no define el `static_assert` macro.

## <a name="syntax"></a>Sintaxis

```cpp
#include <cassert>
```

## <a name="macros"></a>Macros

```cpp
#define assert(E)
```

### <a name="remarks"></a>Comentarios

`assert(E)` solo es constante, si se define NDEBUG donde `assert` por última vez está definido o redefinido, o *E* puede convertir en bool se evalúa como **true**.

## <a name="see-also"></a>Vea también

[assert (macro), _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
