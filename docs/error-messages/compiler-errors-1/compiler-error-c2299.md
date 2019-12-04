---
title: Error del compilador C2299
ms.date: 11/04/2016
f1_keywords:
- C2299
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
ms.openlocfilehash: 009a441ec610053176e79126d9f2663f29b26bc6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759053"
---
# <a name="compiler-error-c2299"></a>Error del compilador C2299

' función ': cambio de comportamiento: una especialización explícita no puede ser un constructor de copias o un operador de asignación de copia

Este error también se puede generar como resultado del trabajo de conformidad del compilador realizado para Visual Studio 2005: las versiones anteriores de Visual C++ permitían especializaciones explícitas para un constructor de copias o un operador de asignación de copia.

Para resolver C2299, no convierta el constructor de copias o el operador de asignación en una función de plantilla, sino en una función que no sea de plantilla que toma un tipo de clase. Cualquier código que llame al constructor de copias o al operador de asignación especificando explícitamente los argumentos de plantilla debe quitar los argumentos de plantilla.

En el ejemplo siguiente se genera C2299:

```cpp
// C2299.cpp
// compile with: /c
class C {
   template <class T>
   C (T t);

   template <> C (const C&);   // C2299
   C (const C&);   // OK
};
```
