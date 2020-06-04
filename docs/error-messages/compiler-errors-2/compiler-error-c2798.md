---
title: Error del compilador C2798
ms.date: 11/04/2016
f1_keywords:
- C2798
helpviewer_keywords:
- C2798
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
ms.openlocfilehash: 6eed1f1aad0783f9e1d5f4126847b54f6b7278e0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739212"
---
# <a name="compiler-error-c2798"></a>Error del compilador C2798

' Super:: Member ' es ambiguo

Varias estructuras heredadas contienen el miembro al que se hace referencia con [Super](../../cpp/super.md). Puede corregir el error:

- Quitando B1 o B2 de la lista de herencia de D.

- Cambiar el nombre del miembro de datos en B1 o B2.

En el ejemplo siguiente se genera C2798:

```cpp
// C2798.cpp
struct B1 {
   int i;
};

struct B2 {
   int i;
};

struct D : B1, B2 {
   void g() {
      __super::i = 4; // C2798
   }
};
```
