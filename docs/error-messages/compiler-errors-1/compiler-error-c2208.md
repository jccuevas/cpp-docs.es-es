---
title: Error del compilador C2208
ms.date: 11/04/2016
f1_keywords:
- C2208
helpviewer_keywords:
- C2208
ms.assetid: 9ae704bc-bf70-45f1-8e47-0470f21edd4e
ms.openlocfilehash: 208e15e98a05089c0e9b1c98400f5267e4f3a48f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758936"
---
# <a name="compiler-error-c2208"></a>Error del compilador C2208

' type ': no hay miembros definidos con este tipo

Un identificador que se resuelve en un nombre de tipo está en una declaración de agregado, pero el compilador no puede declarar un miembro.

En el ejemplo siguiente se genera C2208:

```cpp
// C2208.cpp
class C {
   C;   // C2208
   C(){}   // OK
};
```
