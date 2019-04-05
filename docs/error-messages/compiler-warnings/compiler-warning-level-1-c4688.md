---
title: Advertencia del compilador (nivel 1) C4688
ms.date: 11/04/2016
f1_keywords:
- C4688
helpviewer_keywords:
- C4688
ms.assetid: a027df3c-b2b8-4c49-8539-c2bc42db74e8
ms.openlocfilehash: 1c94198eca0a88174c8655e0d571c37f82a2df36
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781970"
---
# <a name="compiler-warning-level-1-c4688"></a>Advertencia del compilador (nivel 1) C4688

'constraint': la lista de restricciones contiene un tipo privado de ensamblado 'type'

Una lista de restricciones tiene un tipo privado de ensamblado, lo que significa que no estará disponible cuando se acceda al tipo desde fuera del ensamblado. Para más información, vea [Genéricos](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4688.

```
// C4688.cpp
// compile with: /clr /c /W1
ref struct A {};   // private type
public ref struct B {};

// Delete the following 3 lines to resolve.
generic <class T>
where T : A   // C4688
public ref struct M {};

generic <class T>
where T : B
public ref struct N {};
```