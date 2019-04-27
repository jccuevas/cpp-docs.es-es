---
title: Error del compilador C2798
ms.date: 11/04/2016
f1_keywords:
- C2798
helpviewer_keywords:
- C2798
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
ms.openlocfilehash: f3e8f0ac260e49866d1c654f89d34bf57a8ffbc1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152480"
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