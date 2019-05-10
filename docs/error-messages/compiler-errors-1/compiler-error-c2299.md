---
title: Error del compilador C2299
ms.date: 11/04/2016
f1_keywords:
- C2299
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
ms.openlocfilehash: 39659baebf7dc1859a69021f60ed452964ae61af
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447958"
---
# <a name="compiler-error-c2299"></a>Error del compilador C2299

'function': cambio de comportamiento: una especialización explícita no puede ser un constructor de copias o el operador de asignación de copia

Este error también puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual Studio 2005: versiones anteriores de Visual C++ permiten especializaciones explícitas para un constructor de copias o un operador de asignación de copia.

Para resolver C2299, no realice el constructor de copias o el operador de asignación de una función de plantilla, pero en su lugar una función que no son de plantilla que toma un tipo de clase. Cualquier código que llama al constructor de copias o el operador de asignación especificando explícitamente los argumentos de plantilla debe quitar los argumentos de plantilla.

El ejemplo siguiente genera el error C2299:

```
// C2299.cpp
// compile with: /c
class C {
   template <class T>
   C (T t);

   template <> C (const C&);   // C2299
   C (const C&);   // OK
};
```