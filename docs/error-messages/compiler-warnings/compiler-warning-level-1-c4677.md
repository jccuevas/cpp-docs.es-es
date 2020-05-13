---
title: Advertencia del compilador (nivel 1) C4677
ms.date: 11/04/2016
f1_keywords:
- C4677
helpviewer_keywords:
- C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
ms.openlocfilehash: 5b31fd22c917b2c0f505ca189425f8160f62f748
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175550"
---
# <a name="compiler-warning-level-1-c4677"></a>Advertencia del compilador (nivel 1) C4677

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
