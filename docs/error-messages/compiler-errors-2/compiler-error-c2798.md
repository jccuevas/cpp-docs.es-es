---
title: Error del compilador C2798
ms.date: 11/04/2016
f1_keywords:
- C2798
helpviewer_keywords:
- C2798
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
ms.openlocfilehash: f3e8f0ac260e49866d1c654f89d34bf57a8ffbc1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463066"
---
# <a name="compiler-error-c2798"></a>Error del compilador C2798

'super:: miembro' es ambiguo

Varias estructuras heredadas que contienen el miembro al que hace referencia con [super](../../cpp/super.md). Puede resolver el error, ya sea por:

- Quitar de la lista de herencia de D. B1 o B2

- Cambiar el nombre del miembro de datos en la vitamina B1 o B2.

El ejemplo siguiente genera C2798:

```
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