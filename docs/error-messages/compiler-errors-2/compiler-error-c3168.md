---
title: Error del compilador C3168
ms.date: 11/04/2016
f1_keywords:
- C3168
helpviewer_keywords:
- C3168
ms.assetid: 4c36fcfb-c351-48ff-b4eb-78d2aa1b4d55
ms.openlocfilehash: f39160cc09825c6d87d56ff5ba80d21a35f41e12
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676569"
---
# <a name="compiler-error-c3168"></a>Error del compilador C3168

'type': tipo de enumeración subyacente no válido

El tipo subyacente se ha especificado para el `enum` tipo no era válido. El tipo subyacente debe ser un tipo entero de C++ o un tipo CLR correspondiente.

El ejemplo siguiente genera C3168:

```
// C3168.cpp
// compile with: /clr /c
ref class G{};

enum class E : G { e };   // C3168
enum class F { f };   // OK
```
