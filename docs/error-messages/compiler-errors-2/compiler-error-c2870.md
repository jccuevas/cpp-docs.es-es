---
title: Error del compilador C2870
ms.date: 11/04/2016
f1_keywords:
- C2870
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
ms.openlocfilehash: 3b006592723df1222d05e39b3bc9e5729efc8aa6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755036"
---
# <a name="compiler-error-c2870"></a>Error del compilador C2870

' name ': una definición de espacio de nombres debe aparecer en el ámbito de archivo o inmediatamente dentro de otra definición de espacio de nombres

Ha definido el espacio de nombres `name` de forma incorrecta. Los espacios de nombres se deben definir en el ámbito de archivo (fuera de todos los bloques y clases) o inmediatamente dentro de otro espacio de nombres.

En el ejemplo siguiente se genera C2870:

```cpp
// C2870.cpp
// compile with: /c
int main() {
   namespace A { int i; };   // C2870
}
```
