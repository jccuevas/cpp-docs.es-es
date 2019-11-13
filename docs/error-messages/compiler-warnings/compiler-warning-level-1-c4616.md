---
title: ADVERTENCIA del compilador (nivel 1) C4616
ms.date: 11/04/2016
f1_keywords:
- C4616
helpviewer_keywords:
- C4616
ms.assetid: 71e15265-c5bc-42ce-a6a9-4879892472b1
ms.openlocfilehash: 3c13eb28981779e2d089575660d8968c54e4e75f
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051477"
---
# <a name="compiler-warning-level-1-c4616"></a>ADVERTENCIA del compilador (nivel 1) C4616

\#pragma warning: el número de advertencia ' número ' no es una advertencia del compilador válida

No se puede reasignar el número de advertencia especificado en pragma [Warning](../../preprocessor/warning.md) . Se omitió la Directiva pragma.

En el ejemplo siguiente se genera C4616:

```cpp
// C4616.cpp
// compile with: /W1 /c
#pragma warning( disable : 0 )   // C4616
#pragma warning( disable : 999 )   // OK
#pragma warning( disable : 4998 )   // OK
```