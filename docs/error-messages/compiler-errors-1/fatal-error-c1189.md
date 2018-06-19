---
title: Error irrecuperable C1189 | Documentos de Microsoft
ms.custom: ''
ms.date: 04/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1189
dev_langs:
- C++
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 051b7eb965526d12311dfacaeae7a00e4fbe4e75
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199799"
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