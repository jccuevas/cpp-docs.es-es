---
title: Error irrecuperable C1189 | Documentos de Microsoft
ms.custom: ''
ms.date: 04/27/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C1189
dev_langs:
- C++
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b49f227b5fda20ab0ba202d3d7eca99492509b35
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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