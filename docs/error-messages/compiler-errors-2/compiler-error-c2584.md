---
title: Error del compilador C2584
ms.date: 11/04/2016
f1_keywords:
- C2584
helpviewer_keywords:
- C2584
ms.assetid: 836e2c0a-86c0-4742-b432-beb0191ad20e
ms.openlocfilehash: b61ad65555b5d5232468206f6170223c5f160a34
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360481"
---
# <a name="compiler-error-c2584"></a>Error del compilador C2584

'Class': la directa 'Base2' base es inaccesible; ya existe una base de 'Base1'

`Class` ya se deriva directamente de `Base1`. `Base2` También se deriva de `Base1`. `Class` no puede derivar de `Base2` ya que eso significaría heredar (indirectamente) `Base1` nuevo, que no es válido porque `Base1` ya es una clase base directa.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2584.

```
// C2584.cpp
// compile with: /c
struct A1 {
   virtual int MyFunction();
};

struct A2 {
    virtual int MyFunction();
};

struct B1: public virtual A1, virtual A2 {
    virtual int MyFunction();
};

struct B2: public virtual A2, virtual A1 {
    virtual int MyFunction();
};

struct C: virtual B1, B2 {
    virtual int MyFunction();
};

struct Z : virtual B2, virtual C {   // C2584
// try the following line insted
// struct Z : virtual C {
    virtual int MyFunction();
};
```