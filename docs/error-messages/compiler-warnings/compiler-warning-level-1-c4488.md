---
title: Advertencia del compilador (nivel 1) C4488
ms.date: 11/04/2016
f1_keywords:
- C4488
helpviewer_keywords:
- C4488
ms.assetid: 55625e46-ddb5-4c7c-99c7-cd4aa9f879bd
ms.openlocfilehash: c816c1b3f5481ccff19fd2a2377c5fc98f950fee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404083"
---
# <a name="compiler-warning-level-1-c4488"></a>Advertencia del compilador (nivel 1) C4488

'function': requiere ' palabra clave para implementar el método de interfaz 'método_de_interfaz'

Una clase debe implementar todos los miembros de una interfaz de la que hereda directamente. Un miembro implementado debe tener accesibilidad pública y debe marcarse como virtual.

## <a name="example"></a>Ejemplo

C4488 puede producirse si un miembro implementado no es público. El ejemplo siguiente genera la advertencia C4488.

```
// C4488.cpp
// compile with: /clr /c /W1 /WX
interface struct MyI {
   void f1();
};

// implemented member not public
ref class B : MyI { virtual void f1() {} };  // C4488

// OK
ref class C : MyI {
public:
   virtual void f1() {}
};
```

## <a name="example"></a>Ejemplo

C4488 puede producirse si un miembro implementado no está marcado como virtual. El ejemplo siguiente genera la advertencia C4488.

```
// C4488_b.cpp
// compile with: /clr /c /W1 /WX
interface struct MyI {
   void f1();
};

ref struct B : MyI { void f1() {} };   // C4488
ref struct C : MyI { virtual void f1() {} };   // OK
```