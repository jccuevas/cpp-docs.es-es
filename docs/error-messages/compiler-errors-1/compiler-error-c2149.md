---
title: Error del compilador C2149
ms.date: 11/04/2016
f1_keywords:
- C2149
helpviewer_keywords:
- C2149
ms.assetid: 7a106dab-d79f-41b9-85be-f36e86e4d2ab
ms.openlocfilehash: 62eca9730b28f83cea39d5c6606d4bb94ce885dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175215"
---
# <a name="compiler-error-c2149"></a>Error del compilador C2149

'identifier': el ancho del campo de bits con nombre no puede ser igual a cero

Los campos de bits solo pueden tener un ancho de cero si no tienen nombre.

El ejemplo siguiente genera la advertencia C2149:

```
// C2149.cpp
// compile with: /c
struct C {
   int i : 0;   // C2149
   int j : 2;   // OK
};
```