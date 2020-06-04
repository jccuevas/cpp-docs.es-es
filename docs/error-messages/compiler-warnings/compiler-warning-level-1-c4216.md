---
title: Advertencia del compilador (nivel 1) C4216
ms.date: 11/04/2016
f1_keywords:
- C4216
helpviewer_keywords:
- C4216
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
ms.openlocfilehash: 2521366a9f33e8c5b1b7d41951a7cb08adfc2561
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199828"
---
# <a name="compiler-warning-level-1-c4216"></a>Advertencia del compilador (nivel 1) C4216

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
