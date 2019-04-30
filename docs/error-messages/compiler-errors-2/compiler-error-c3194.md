---
title: Error del compilador C3194
ms.date: 11/04/2016
f1_keywords:
- C3194
helpviewer_keywords:
- C3194
ms.assetid: 49d3ffc6-eff6-4b46-865b-18811692a8bb
ms.openlocfilehash: 181a18dde45c3363f1f77bc0cbbd5b0ffca3e898
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397463"
---
# <a name="compiler-error-c3194"></a>Error del compilador C3194

'member': un tipo de valor no puede tener un operador de asignación

No se admiten las funciones miembro especiales que requieren la invocación automática por el compilador, como un constructor de copias o un operador de asignación de copia dentro de una clase de valor.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3194.

```
// C3194.cpp
// compile with: /clr /c
value struct MyStruct {
   MyStruct& operator= (const MyStruct& i) { return *this; }   // C3194
};

ref struct MyStruct2 {
   MyStruct2% operator= (const MyStruct2% i) { return *this; }   // OK
};
```