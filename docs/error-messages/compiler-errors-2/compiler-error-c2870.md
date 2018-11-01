---
title: Error del compilador C2870
ms.date: 11/04/2016
f1_keywords:
- C2870
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
ms.openlocfilehash: f61281da23e46236e7fce496a4d89086e5d6c0ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546384"
---
# <a name="compiler-error-c2870"></a>Error del compilador C2870

'name': una definición de espacio de nombres debe aparecer en el ámbito de archivo o directamente dentro de otra definición de espacio de nombres

Define el espacio de nombres `name` incorrectamente. Los espacios de nombres deben definirse en el ámbito de archivo (fuera de todos los bloques y clases) o inmediatamente dentro de otro espacio de nombres.

El ejemplo siguiente genera C2870:

```
// C2870.cpp
// compile with: /c
int main() {
   namespace A { int i; };   // C2870
}
```