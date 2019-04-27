---
title: Error del compilador C2870
ms.date: 11/04/2016
f1_keywords:
- C2870
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
ms.openlocfilehash: f61281da23e46236e7fce496a4d89086e5d6c0ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165052"
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