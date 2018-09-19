---
title: Error del compilador C2801 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2801
dev_langs:
- C++
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d57ee5bf5f5152ef55852c9f9b829bc4a1d17d41
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040640"
---
# <a name="compiler-error-c2801"></a>Error del compilador C2801

'operator operator' debe ser un miembro no estático

Únicamente como miembros no estáticos se pueden sobrecargar los operadores siguientes:

- Asignación `=`

- Acceso a miembros de clase `->`

- Subíndices `[]`

- Llamada de función `()`

Posibles causas de C2801:

- Operador sobrecargado no es una clase, estructura o miembro de unión.

- Operador sobrecargado se declara `static`.

- El ejemplo siguiente genera C2801:

```
// C2801.cpp
// compile with: /c
operator[]();   // C2801 not a member
class A {
   static operator->();   // C2801 static
   operator()();   // OK
};
```