---
title: ADVERTENCIA del compilador (nivel 2) C4094
ms.date: 11/04/2016
f1_keywords:
- C4094
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
ms.openlocfilehash: c293522e5d60d0edb4cc2da289e0ece71f89329f
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052201"
---
# <a name="compiler-warning-level-2-c4094"></a>ADVERTENCIA del compilador (nivel 2) C4094

' token ' sin etiqueta declarado no tiene símbolos

El compilador detectó una declaración vacía mediante una estructura, una Unión o una clase sin etiquetar. Se omite la declaración.

## <a name="example"></a>Ejemplo

```cpp
// C4094.cpp
// compile with: /W2
struct
{
};   // C4094

int main()
{
}
```

Esta condición genera un error en la compatibilidad con ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).