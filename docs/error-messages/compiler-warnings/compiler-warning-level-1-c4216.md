---
title: ADVERTENCIA del compilador (nivel 1) C4216
ms.date: 11/04/2016
f1_keywords:
- C4216
helpviewer_keywords:
- C4216
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
ms.openlocfilehash: 69559348a27151a22b11cae8d821110d923cd803
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627338"
---
# <a name="compiler-warning-level-1-c4216"></a>ADVERTENCIA del compilador (nivel 1) C4216

se ha utilizado una extensión no estándar: Float Long

Las extensiones predeterminadas de Microsoft (/ZE) tratan **float Long** como **Double**. La compatibilidad con ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)) no. Utilice **Double** para mantener la compatibilidad. En el ejemplo siguiente se genera C4216:

```cpp
// C4216.cpp
// compile with: /W1
float long a;   // C4216

// use the line below to resolve the warning
// double a;

int main() {
}
```