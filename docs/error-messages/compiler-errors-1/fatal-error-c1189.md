---
title: Error irrecuperable C1189
ms.date: 04/27/2018
f1_keywords:
- C1189
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
ms.openlocfilehash: 06d42316a0109ac063bba43cefebd9aab71c2e72
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565534"
---
# <a name="fatal-error-c1189"></a>Error irrecuperable C1189

> **\#Error:** *mensaje de error proporcionado por el usuario*

## <a name="remarks"></a>Comentarios

Genera el error C1189 el `#error` directiva. El desarrollador que codifica la directiva especifica el texto del mensaje de error. Para obtener más información, consulte [#error (directiva) (C/C ++)](../../preprocessor/hash-error-directive-c-cpp.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C1189. En el ejemplo, el desarrollador emite un mensaje de error personalizado porque el `_WIN32` no está definido el identificador:

```cpp
// C1189.cpp
#undef _WIN32
#if !defined(_WIN32)
#error _WIN32 must be defined   // C1189
#endif
```

## <a name="see-also"></a>Vea también

[#define (directiva) (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)