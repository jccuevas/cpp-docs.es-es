---
title: Error del compilador C3075
ms.date: 11/04/2016
f1_keywords:
- C3075
helpviewer_keywords:
- C3075
ms.assetid: f431daa9-e0fa-48f0-a5c3-f99be96b55e3
ms.openlocfilehash: 345cdd17b9da0be8f8d6e9f7b5f48624ade412bd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761587"
---
# <a name="compiler-error-c3075"></a>Error del compilador C3075

'instance': no puede insertar una instancia de un tipo de referencia ('type') en un tipo de valor

Un tipo de valor no puede contener una instancia de un tipo de referencia.

Para obtener más información, vea [ C++ semántica de pila para los tipos de referencia](../../dotnet/cpp-stack-semantics-for-reference-types.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3075.

```cpp
// C3075.cpp
// compile with: /clr /c
ref struct U {};
value struct X {
   U y;   // C3075
};

ref struct Y {
   U y;   // OK
};
```
