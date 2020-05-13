---
title: ADVERTENCIA del compilador (nivel 1) C4183
ms.date: 11/04/2016
f1_keywords:
- C4183
helpviewer_keywords:
- C4183
ms.assetid: dc48312c-4b34-44dd-80ff-eb5f11d5ca47
ms.openlocfilehash: 4c2c7ce23cfaea5ebf31e78d84b7ff7fbdbf4c85
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175940"
---
# <a name="compiler-warning-level-1-c4183"></a>ADVERTENCIA del compilador (nivel 1) C4183

' Identifier ': falta el tipo de valor devuelto; se supone que es una función miembro que devuelve ' int '

La definición en línea de una función miembro de una clase o una estructura no tiene un tipo de valor devuelto. Se supone que esta función miembro tiene un tipo de valor devuelto predeterminado de `int`.

En el ejemplo siguiente se genera C4183:

```cpp
// C4183.cpp
// compile with: /W1 /c
#pragma warning(disable : 4430)
class MyClass1;
class MyClass2 {
   MyClass1() {};   // C4183
};
```
