---
title: Error irrecuperable C1189
ms.date: 04/27/2018
f1_keywords:
- C1189
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
ms.openlocfilehash: 2217b865109cc48151e4e96b2d38b88764c0c64f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203659"
---
# <a name="fatal-error-c1189"></a>Error irrecuperable C1189

> **error de\#:** *mensaje de error proporcionado* por el usuario

## <a name="remarks"></a>Observaciones

C1189 se genera mediante la Directiva `#error`. El desarrollador que codifica la Directiva especifica el texto del mensaje de error. Para obtener más información, vea [#error (Directiva)C++(C/)](../../preprocessor/hash-error-directive-c-cpp.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C1189. En el ejemplo, el desarrollador emite un mensaje de error personalizado porque no se ha definido el identificador de `_WIN32`:

```cpp
// C1189.cpp
#undef _WIN32
#if !defined(_WIN32)
#error _WIN32 must be defined   // C1189
#endif
```

## <a name="see-also"></a>Consulte también

[#define (directiva) (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)
