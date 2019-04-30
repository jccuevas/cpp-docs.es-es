---
title: Advertencia del compilador (nivel 4) C4625
ms.date: 11/04/2016
f1_keywords:
- C4625
helpviewer_keywords:
- C4625
ms.assetid: 4cc99e50-846c-4784-97da-48b977067851
ms.openlocfilehash: edcb43bf11c073e6ce721ba999fd99d28a8df15d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62220499"
---
# <a name="compiler-warning-level-4-c4625"></a>Advertencia del compilador (nivel 4) C4625

'derived class': el constructor de copias se definió implícitamente como eliminado porque un constructor de copias de clase base es inaccesible o se ha eliminado

Se eliminó un constructor de copias o no está accesible en una clase base y, por tanto, no se generó para una clase derivada. Cualquier intento de copiar un objeto de este tipo provocará un error del compilador.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

## <a name="example"></a>Ejemplo

El siguiente ejemplo genera el error C4625 y muestra cómo corregirlo.

```
// C4625.cpp
// compile with: /W4 /c
#pragma warning(default : 4625)

struct A {
   A() {}

private:
   A(const A&) {}
};

struct C : private virtual A {};
struct B :  C {};   // C4625 no copy constructor

struct D : A {};
struct E :  D {};   // OK
```