---
title: ADVERTENCIA del compilador (nivel 1) C4677
ms.date: 11/04/2016
f1_keywords:
- C4677
helpviewer_keywords:
- C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
ms.openlocfilehash: 8567e7392537507a25121977448ac47ec079316b
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051376"
---
# <a name="compiler-warning-level-1-c4677"></a>ADVERTENCIA del compilador (nivel 1) C4677

' función ': la signatura de un miembro no privado contiene un tipo privado de ensamblado ' private_type '

Un tipo que tiene accesibilidad pública fuera del ensamblado usa un tipo que tiene acceso privado fuera del ensamblado. Un componente que hace referencia al tipo de ensamblado público no podrá usar el miembro de tipo o los miembros que hagan referencia al tipo privado de ensamblado.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4677.

```cpp
// C4677.cpp
// compile with: /clr /c /W1
delegate void TestDel();
public delegate void TestDel2();

public ref class MyClass {
public:
   static event TestDel^ MyClass_Event;   // C4677
   static event TestDel2^ MyClass_Event2;   // OK
};
```