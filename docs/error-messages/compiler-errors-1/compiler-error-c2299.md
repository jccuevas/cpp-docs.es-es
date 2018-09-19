---
title: Error del compilador C2299 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2299
dev_langs:
- C++
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4977f4a5ac81cf4c04d3b143f6f7e670a9d9279
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049623"
---
# <a name="compiler-error-c2299"></a>Error del compilador C2299

'function': cambio de comportamiento: una especialización explícita no puede ser un constructor de copias o el operador de asignación de copia

Este error también puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual C++ 2005: versiones anteriores de Visual C++ permiten las especializaciones explícitas para un constructor de copias o un operador de asignación de copia.

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