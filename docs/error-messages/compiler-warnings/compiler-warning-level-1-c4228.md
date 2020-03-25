---
title: Advertencia del compilador (nivel 1) C4228
ms.date: 11/04/2016
f1_keywords:
- C4228
helpviewer_keywords:
- C4228
ms.assetid: 9301d660-d601-464e-83f5-7ed844a3c6dc
ms.openlocfilehash: c216143f2b47148f73502c847175201ea9a74fee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175901"
---
# <a name="compiler-warning-level-1-c4228"></a>Advertencia del compilador (nivel 1) C4228

se ha utilizado una extensión no estándar: se omiten los calificadores después de la coma en la lista de declaradores

El uso de calificadores como **const** o `volatile` después de una coma al declarar variables es una extensión de Microsoft ([/ze](../../build/reference/za-ze-disable-language-extensions.md)).

## <a name="example"></a>Ejemplo

```cpp
// C4228.cpp
// compile with: /W1
int j, const i = 0;  // C4228
int k;
int const m = 0;  // ok
int main()
{
}
```
